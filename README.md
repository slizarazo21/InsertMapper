# InsertMapper

InsertMapper is a bioinformatic pipeline useful for identifying partial and full insertion sites in the genome. 
The pipeline, as it is, requires:
1. A FASTA file generated that contains information about the primers used in the nested PCR
2. A fasta file of the whole human genome
3. A bowtie index, both FASTA and index files should be from the same assembly
4. A plasmid index

Briefly, the pipeline does the following:
1. Selects reads that contain the primers sequences present in the inserted construct
2. Removes duplicates
3. Removes reads that align to the plasmid
4. Clips primers sequences from reads
5. Align reads to the genome of interest
6. Extract and merge coordinates for those reads in the genome.
7. Identifies potential regions of insertion by mapping sequences that matches known insertion sequences. For example, PiggyBac insertions happen at TTAA sequences; therefore, the pipeline keeps reads that contain only those sequences.
8. Extracts counts on those defined regions from the filtered reads and considers the total number of potential insertion sequences (e.g. TTAA). While doing this, considers a background read density for statistical analysis.
9. Computes a partial insertion site analysis.
10. Computes a full insertion site analysis by looking at the intersection of defined partial insertion sites
