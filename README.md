# WGS to VCF Converter

This program can be used to convert whole genome sequence data stored in a BigQuery table with the Institute for Systems Biology.  This covers over 1000 patient samples that have been processed against HG19 and are available for use for credentialed researchers.

## Preparation
To use this script, you first must set up your environment to support BigQuery through ISG.  We recommend that you set up a virtual environment (not covered here).

### Install required software
The following software must be installed to support this script

- Google Cloud BigQuery Libraries:
`python -m pip install --upgrade google-cloud-bigquery`

### Create a proper key and set up your environment
Your environment and access key can be set up following the directions at: 
- https://cloud.google.com/bigquery/docs/quickstarts/quickstart-client-libraries#client-libraries-install-python

## Command Line Usage
Usage information can be printed out by running the program with the help flag:
`python wgs_to_vcf.py --help`

```
usage: wgs_to_vcf.py [-h] [--output_file OUTPUT_FILE] [--chromosome {chr19,chrX,chrY,chr6,chr18,chr14,chr7,chr12,chr17,chr2,chr9,chr1,chr5,chr10,chr20,chr22,chr8,chr15,chr3,chr16,chr13,chr21,chr11,chr4}] [--limit LIMIT] tcga_id

positional arguments:
  tcga_id               TCGA ID to generate a vcf file from.

optional arguments:
  -h, --help            show this help message and exit
  --output_file OUTPUT_FILE, -o OUTPUT_FILE
                        Set the output vcf file name.
  --chromosome {chr19,chrX,chrY,chr6,chr18,chr14,chr7,chr12,chr17,chr2,chr9,chr1,chr5,chr10,chr20,chr22,chr8,chr15,chr3,chr16,chr13,chr21,chr11,chr4}
                        Limit to a specific chromosome.
  --limit LIMIT, -l LIMIT
                        Limit the number of SNVs returned (for debugging primarily).

```

### Example usage
The required parameter is the TCGA ID of interest.  For example:

`python wgs_to_vcf.py TCGA-44-2656`

You can also limit to a specific chromosome of interest.  For example:

`python wgs_to_vcf.py TCGA-44-2656 --chromosome chr4`

The chromosomes which are allowed are listed in the help above.  Chromosome format is in the 'chr#' syntax.

And finally, you can also limit the number of entries for testing or debugging purposes.

`python wgs_to_vcf.py TCGA-44-2656 --chromosome chr4 --limit 20`