# OWASjoint `v0.1.0`
OWAS-joint, a framework for multi-cell-type openness-weighted association studies for trait-associated genomic segments prioritization.

OWAS-joint is an extension of the OWAS method (https://github.com/shuangsong0110/OWAS), which provides multi-cell-type aggregation, visualization, and pathway enrichment analysis.


## Run OWAS-joint

```r
library(OWASjoint)
run.owas.joint(ctype=CELLTYPE (required),
     weight= ACAT_WEIGHTS (optional),
	   trait = TRAIT_NAME(required),
	   path.owas=PATH_TO_OWAS_ANALYSIS (required), 
	   chr=CHROMOSOME (optional))                    
```
- CELLTYPE (required): a vector containing all cell types that need to be aggregated. Please Note that OWAS analysis has to be performed before aggregation. See https://github.com/shuangsong0110/OWAS.

- ACAT_WEIGHTS: If not specified, OWAS-joint will use equal ACAT weights for all cell types.

- TRAIT_NAME: the name of the trait. Need to be the same with the input of OWAS analysis (`run.owas`).

- PATH_TO_OWAS_ANALYSIS: The PATH of single-cell-type OWAS analysis. Need to be the same with the input of OWAS analysis (`run.owas`).

- CHROMOSOME： By default=1:22

## Output 

The `run.owas.joint` function returns a data.frame with 7 columns in path.owas/ctype/JOINT/:

`gene`: Gene name

`id`: Index of the segment on that gene

`snplen`: The number of SNPs on the segment

`p_g`: p-value

`chr`: Chromosome

`start`: Segment start position (hg19)

`end`: Segment end position (hg19)

## Visualization

### Visualization for OWAS-joint (Manhattan plot)
```r
owas.joint.plot(trait = TRAIT_NAME(required),
	   path.owas=PATH_TO_OWAS_ANALYSIS (required), 
	   path=OUTPUT_DIR (required, and has to be same with the PATH in get.cov),
	   chr=CHROMOSOME (optional))                    
```

- TRAIT_NAME: the name of the trait. Need to be the same with the input of OWAS analysis (`run.owas`).

- PATH_TO_OWAS_ANALYSIS: The PATH of single-cell-type OWAS analysis. Need to be the same with the input of OWAS analysis (`run.owas`).

- OUTPUT_DIR: path to the manhattan plot

- CHROMOSOME： By default=1:22

![multi](/Rectangular-Manhattan.ACAT_part.png)



### Visualization for single-cell-type OWAS (Manhattan plot)
```r
owas.single.plot(trait = TRAIT_NAME(required),
     ctype= CELL_TYPE (required),
	   path.owas=PATH_TO_OWAS_ANALYSIS (required), 
	   path=OUTPUT_DIR (required, and has to be same with the PATH in get.cov),
	   chr=CHROMOSOME (optional))                    
```

- TRAIT_NAME: the name of the trait. Need to be the same with the input of OWAS analysis (`run.owas`).

- CELL_TYPE: can be either an element or a vector including mutliple cell types. We suggest less than four cell types for better visualization.

- PATH_TO_OWAS_ANALYSIS: The PATH of single-cell-type OWAS analysis. Need to be the same with the input of OWAS analysis (`run.owas`).

- OUTPUT_DIR: path to the manhattan plot

- CHROMOSOME： By default=1:22

![single](/Circular-Manhattan.A549.Helas3.Hepg2.Th1.png)


## :busts_in_silhouette: Maintainer

Please contact Shuang Song (song-s19@mails.tsinghua.edu.cn) if there are any problems or questions.






