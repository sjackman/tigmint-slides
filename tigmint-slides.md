---
author: 'Shaun D Jackman'
date: '2017-07-24'
history: true
slideNumber: true
---

## Tigmint

### Correct Misassemblies Using Linked Reads From Large Molecules

**Shaun Jackman** [\@sjackman][]

Benjamin P Vandervalk, Rene L Warren, Hamid Mohamadi, Justin Chu, Sarah Yeo, Lauren Coombe, Joerg Bohlmann, Steven JM Jones, Inanc Birol

ISMB HiTSeq 2017-07-24&mdash;25

<https://sjackman.ca/tigmint-slides>

[![Creative Commons Attribution License](images/cc-by.png)][cc-by]

[\@sjackman]: http://twitter.com/sjackman
[cc-by]: http://creativecommons.org/licenses/by/4.0/

## Shaun Jackman

| [BCCA Genome Sciences Centre][]
| Vancouver, Canada
| [\@sjackman][] | [github.com/sjackman][] | [sjackman.ca][]

![](images/sjackman.jpg)

[BCCA Genome Sciences Centre]: http://bcgsc.ca
[github.com/sjackman]: https://github.com/sjackman
[sjackman.ca]: http://sjackman.ca

10x Genomics Chromium
================================================================================

## Utility of large molecules and linked reads

+ One library rather than two: \
  Illumina paired-end and mate-pair

----------------------------------------

![10x Genomics Chromium Linked Reads <http://www.10xgenomics.com/assembly/>](images/10xgenomics.png)

## Scaffolding with ARCS

----------------------------------------

![ARCS <https://github.com/bcgsc/arcs>](images/arcs.png)

## Misassemblies limit scaffold contiguity

for highly contiguous assemblies

## Tigmint

## Visualization

+ sequence segment graph
+ physical molecule coverage
+ molecule start and end scatter plot

## Identifying and fixing misassemblies

## Menagerie of Misassemblies

+ Missing sequence (deletion)
+ Inversion
+ Chimeric sequence
+ Collapsed repeat
+ Insertion

## Genome Skimming

Assemble the 6 Mbp Sitka spruce mitochondrion

+ Whole genome sequencing data contains both nuclear and organellar reads
+ Each cell contains hundreds of mitochondria and plastids
+ Reads of the organellar genomes are abundant
+ Organellar sequences assemble well with a single lane
+ Single-copy nuclear sequences are too low depth to assemble well

----------------------------------------

![White spruce depth vs percent GC](images/picea-glauca-depth-gc.png)

Sitka Spruce Mitochondrion
================================================================================

## Aim

Assemble the Sitka spruce mitochondrion into a single scaffold\* using 10x Chromium data and annotate it.

\* if it has a single chromosome

## Method

+ Assemble the reads with [ABySS][]
+ Correct misassemblies with [Tigmint][]
+ Scaffold with [ARCS][] and [LINKS][]
+ Annotate genes with [MAKER][] and [Prokka][]

## Results

+ Largest scaffold is 1.2 Mbp
+ 50% of the 6 Mbp genome in 4 scaffolds > 460 kbp
+ 75% of the genome in 13 scaffolds > 100 kbp
+ 1/223 or 0.45% of reads are mitochondrial
+ 115 ORFs with similarity to known mitochondrial genes
+ 1,154 other ORFS ≥ 300 bp
+ 9 Type II introns in 6 genes

----------------------------------------

![Sitka spruce mitochondrion](images/picea-sitchensis-mitochondrion.png)

fin
================================================================================

## Shaun Jackman

| [BCCA Genome Sciences Centre][]
| Vancouver, Canada
| [\@sjackman][] | [github.com/sjackman][] | [sjackman.ca][]

**Slides** \
<https://sjackman.ca/tigmint-slides>

**Markdown source code** \
<https://github.com/sjackman/tigmint-slides>

## Links

[ABySS][]
&middot; [ARCS][]
&middot; [Architect][]
&middot; [Fragscaff][]
&middot; [LINKS][]
&middot; [LongRanger][]
&middot; [MAKER][]
&middot; [Pilon][]
&middot; [Prokka][]
&middot; [RNAweasel][]
&middot; [Sealer][]
&middot; [Supernova][]
&middot; [Tigmint][]

[ABySS]: https://github.com/bcgsc/abyss
[ARCS]: https://github.com/bcgsc/arcs
[Architect]: https://github.com/kuleshov/architect
[Fragscaff]: http://krishna.gs.washington.edu/software.html
[Kollector]: https://github.com/bcgsc/kollector
[LINKS]: https://github.com/warrenlr/LINKS
[LongRanger]: https://support.10xgenomics.com/genome-exome/software/pipelines/latest/what-is-long-ranger
[MAKER]: http://www.yandell-lab.org/software/maker.html
[Pilon]: http://www.broadinstitute.org/software/pilon/]
[Prokka]: http://www.vicbioinformatics.com/software.prokka.shtml
[RNAweasel]: http://megasun.bch.umontreal.ca/RNAweasel/
[Sealer]: https://github.com/bcgsc/abyss/tree/master/Sealer
[Supernova]: http://support.10xgenomics.com/de-novo-assembly/software/overview/welcome
[Tigmint]: https://github.com/bcgsc/tigmint

Supplementary Slides
================================================================================

## Scaffolding Tools for 10x

+ [ARCS][] with [LINKS][]
+ [Architect][] \
  intended for synthetic long reads
+ [Fragscaff][] \
  intended for contiguity-preserving transposition

----------------------------------------

| Read Metrics                    | Plastid         | Mitochondrion
|---------------------------------|-----------------|--------------
| Number of HiSeq lanes           | 1 GemCode lane  | 1 Chromium lane
| Read length                     | 2 x 125 bp      | 2 x 150 bp
| Number of read                  | 630 million     | 843 million
| Number selected for assembly    | 4.3 million     | 119 million
| Number mapped to assembly       | 15,232 of 4.3 M | 3.78 M of 843 M
| Proportion of organellar reads  | 1/283 0.35%     | 1/223 or 0.45%
| Depth of coverage               | 17x             | 40x

----------------------------------------

| Assembly Metrics                | Plastid         | Mitochondrion
|---------------------------------|-----------------|--------------
| Assembled genome size           | 124,029 bp      | 6.09 Mbp
| Number of contigs               | 1 contig        | 1,216 contigs
| Contig N50                      | 124 kbp         | 13.7 kbp
| Number of scaffolds             | 1 scaffold      | 239 scaffolds
| Scaffold N50                    | 124 kbp         | 461 kbp
| Largest scaffold                | 124 kbp         | 1,223 kbp
| GC content                      | 38.8%           | 43.6%

----------------------------------------

| Annotation Metrics          | Plastid   | Mitochondrion
|-----------------------------|-----------|--------------
| Number of genes w/o ORFS    | 114 (108) | 115 (67)
| Protein-coding genes (mRNA) | 74 (72)   | 84 (47)
| rRNA genes                  | 4 (4)     | 3 (2)
| tRNA genes                  | 36 (32)   | 25 (18)
| ORFs ≥ 300 bp               | 4         | 1,154
| Introns in coding genes     | 9 (8)     | 9 (6)
| Introns in tRNA genes       | 6 (6)     | 0
