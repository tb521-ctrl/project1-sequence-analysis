# project1-sequence-analysis
Project one uses Python to analyse DNA sequencing reads from fission yeast (S.pombe). It identifies nucleotide mismatches and investigates whether samples that are treated with a genotoxic agent are different from an untreated control.
To run the programme, open the notebook in Google Colab. Download and load reference.txt and reads.csv. Next, run the five function cells and the cell that calculates the statisitcs and the final anaylsis cell. 
reference.txt contains 200 nucleotide reference sequences. reads.csv contains 6,000 aligned reads from six samples. Three samples are treatment and three are control. The program reports read validity, mismatch positions and base changes. It prints group tables with valid and invalid read counts, mismatch percentages, most frequently mutated positions and substitution counts. The tables also display gorup averages, differences and Welch's t-test results. 

The programme is split into five functions so each stage is tested separately. I reused codes analyse_reads(), validate_reads() and find_mutations() rather than repeating code. 
I used dictionaries to store counts for each sample, substitutions and positions because they allow counts to be updated using .get() without creating a fixed list of possible mutations. 
Invalid reads are retained with their errors but excluded from mutation percentages, which are calculated using valid reads only. If a sample has no valid reads, the percentage is None so that results aren't divided by 0. 
When positions have equal mismatch counts, I chose the earlier position first. For statistical comparisons, I used one percentage per biological sample instead of treating thousands of reads as independent samples. 
Assert statement are used to check lowercase conversion, invalid characters and incorrect sequence length, this includes reads with two errors. Mutations for first and last position were detected. I tested the empty output, samples with no valid reads and more than one experimental group. I tested the position-comparison function using a small dataset with known mismatch counts. 

