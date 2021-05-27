# XRRpred-docker
This is the docker version of the [XRRpred](http://biomine.cs.vcu.edu/servers/XRRPred/) : predictor of resolution and r-free in protein X-ray crystallography

this is a self-contained repository and only need a docker implementation to run. 

## Instructions for running XRRpred
after coloning (or downloading and extracting) the repository, the next step is to build the image by entering the following command in the root folder of the repository:
```
docker build -t xrrpred docker_context -f XRRpred.dockerfile
```
This creates a docker image named `xrrpred`. 
To run XRRpred on an input fasta, you should enter the following command:
```
docker run -i  xrrpred XRRpred/dockerinout < example.fasta > results.tar.gz
```

`example.fasta` is the path to input file and `results.tar.gz` is the path to output file.
(input fasta file should be formatted like the file `example.fasta` included in the repostiory)

### format of input fasta file:
XRRPred accepts one or more proteins as input. The input protein sequences should be in the FASTA format, where for the multiple-chain proteins the chain sequences must use the same prefix in their ID (before the underscore). Example below shows the formatting for two proteins where proteinID1 has two chains (chainID1 and chainID2) and proteinID2 has one chain.

```
>proteinID1_chainID1
AMINOACIDSEQUENCE
>proteinID1_chainID2
AMINOACIDSEQUENCE
>proteinID2
AMINOACIDSEQUENCE
```

you can also look at the example file `example.fasta`

### Output
the output is produced in a tar archive including the csv resutls and the visualizations. you can find an example output included in the repository (`example_results.tar.gz`)
