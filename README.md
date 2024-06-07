## CMSclassifier

An R package and an example data set are provided to run the CMSclassifier. 

To install the CMSclassifier, install from github using devtools:
```
library(devtools)
install_github("Sage-Bionetworks/CMSclassifier")
```

To run the demo below, you will need a Synapse account and the Synapse R client installed:
```
install.packages("synapser", repos = c("http://ran.synapse.org", "http://cran.fhcrc.org"))
```

Alternatively, edit your ~/.Rprofile and configure your default repositories:
```
options(repos = c("http://ran.synapse.org", "http://cran.fhcrc.org"))
```
after which you may run install.packages without specifying the repositories:
```
install.packages("synapser")
```

Both classifiers (Random forest and single sample) expect data formatted according to the example data set provided:
```
library(synapser)
library(CMSclassifier)

synLogin(authToken="[acquired access token from Synapse]")

sampleData <- read.table(synGet("syn4983432")$path, sep="\t",header = TRUE,row.names = 1,check.names=FALSE)

Rfcms <- CMSclassifier::classifyCMS(t(sampleData),method="RF")[[3]]
SScms <- CMSclassifier::classifyCMS(t(sampleData),method="SSP")[[3]]
```


