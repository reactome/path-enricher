# path-enricher

This repository contains scripts to find enriched paths and code to calculate path scores based on protein co-expression from CoXpresDB

## Disease_Path_Analysis.ipynb

This Jupyter notebook:
1. builds a reactions network based on curated and predicted reactions connections
2. identifies start and end reactions based on graph properties (degrees)
3. calculates shortest paths between start and end reactions
4. uses disease-associated-genes data to calculate enriched paths
  1. obtain gene list from DisGeNet
  2. match UniProt IDs with reactions in path
  3. calculate the number of disease-related reactions in path
  4. calculate overall path score based on disease vs normal reactions in path
  5. the higher the score the more enriched the path in the disease

## CoXpresDB_Path_Scorer.ipynb

This Jupyter notebook:
1. retrieves all UniProt IDs from Reactome using neo4j
2. converts UniProt to Entrez IDs using UniProt API
3. imports protein co-expression data from CoXpresDB
4. calculates path score based on protein co-expression values
  1. sets of proteins are created based on reactions in Reactome
  2. protein co-expressions are converted into reaction co-expressions based on previous step
  3. path score is calculated by considering pair-wise reaction co-expressions in the path
  4. the lower the score the more similar the expression of proteins in the path
