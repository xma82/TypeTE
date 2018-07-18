# reGenotypeTE
This pipeline is currenly under construction by Jainy Thomas (University of Utah) and Clement Goubert (Cornell University).
Elaborated with the collaboration of Jeffrey M. Kidd (University of Michigan)

## Purpose

reGenotypeTE is a pipeline dedicated to re-genotype Mobile Element Insertion (MEI) previously scored with MELT (Mobile Element Locator Tool, ). reGenotypeTE extracts reads from previously detected polymorphic MEI and performs using populations data a local re-assembly of both presence and absence loci. Eventually, remapping of the reads at the infividual level allow to score the genotype of the MEI using a modified version of Li's et al. genotype likelihood. This method drammatically improves the quality of the genotypes of reported MEI and can be directly used after a MELT run on both de-novo (non-reference) and deletion (reference) insertions.

## Installation

### Dependencies

These programs need to be installed and their path reported in the file "parameterfile.init"
Perl executable must be in the user path

* PERL https://www.perl.org/
* PARALLEL https://www.gnu.org/software/parallel/
* PICARD https://broadinstitute.github.io/picard/
* BEDTOOLS http://bedtools.readthedocs.io/en/latest/
* SEQTK https://github.com/lh3/seqtk
* BAMUTILS https://genome.sph.umich.edu/wiki/BamUtil
* SPADES http://cab.spbu.ru/software/spades/
* MINIA http://minia.genouest.org/
* CAP3 http://seq.cs.iastate.edu/cap3.html
* BLAST ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/
* BWA http://bio-bwa.sourceforge.net/bwa.shtml
* BGZIP http://www.htslib.org/doc/bgzip.html
* TABIX http://www.htslib.org/doc/tabix.html

### Download and install

Clone from git repository:

```sh
git clone https://github.com/clemgoub/reGenotypeTE
cd reGenotypeTE
```

### De-novo insertion (non-reference)

## File preparation
1. a vcf/vcf.gz file generated by the MELT discovery workflow. If the loci/individuals are sampled from the original vcf/vcf.gz use the following flag `--INFO-ALL` in vcftools so the subsetted vcf will be compatible with reGenotypeTE

2. bam files for each individual found in the vcf file

3. a two column tab separated table with the sample name and corresponding bam name:

```
sample1 sample1-xxx-file.bam
sample2 sample2-yyy-file.bam
sample3 sample3-zzz-file.bam
```
4. Reference genome in fasta format (to date tested with hg19 and hg38)

5. Edit the file "parameterfile.init" following the indications within.

## Run reGenotypeTE

Once your files are ready and parameterfile.init properly filled, run the following command in the reGenotypeTE folder:

```sh
nohup ./run_reGenotypeTE.sh &> reGenotypeTE.log
```
### Deletions (reference-insertions)
Soon! We are currently testing it!
