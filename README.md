# Ontology and Knowledge Graph of 22 Favorite English Songs

This project builds an RDF knowledge graph of 22 favorite English songs using semantic web technologies, combining external vocabularies (e.g., `schema`, `dbr`) with custom ontologies (`myOnto`) and personal resources (`mySemantics`). The graph is designed, queried, and visualized through SPARQL, SHACL, and GraphDB tools.

> **Course**: Semantic Web and Linked Data  
> **Institution**: University of Zurich (Spring 2023)  
> **Contributors**: Xiaojing Zhang and one teammate

---

## Project Structure

```text
project-root/
│
├── classes_properties.ttl      # Custom ontology (myOnto) definitions and property constraints
├── resources.ttl               # RDF triples representing 22 songs and related entities
├── metadata.xlsx               # Song metadata collected from Wikipedia and Spotify
├── data_model.graphml          # Ontology diagram for visualization in GraphDB or Gephi
│
├── script.ipynb                # Notebook for uploading RDF data and running SPARQL queries
├── shacl.ipynb                 # SHACL validation rules and conformance report
│
├── Project Report.pdf          # Full report describing data modeling, queries, visualizations
└── README.md                   # This file
```


---

## Project Goals

- Represent 22 English songs as RDF resources using Turtle format  
- Define and apply a custom ontology (`myOnto`) for music metadata  
- Integrate resources from DBpedia (`dbr`) and `schema.org` with manually created ones (`mySemantics`)  
- Query the graph using SPARQL and SPARQL*  
- Validate structure and constraints using SHACL  
- Visualize structure and genre distributions in GraphDB  

---

## Ontology: `myOnto`

- **Custom classes**: `myOnto:Song`, `myOnto:Person`, etc.  
- **Custom properties**: `myOnto:hasName`, `myOnto:hasWikipageID`  
- **Constraints**:
  - `myOnto:Person` must have exactly one `hasWikipageID` (type: integer)  
  - Uses `owl:FunctionalProperty` and `owl:InverseFunctionalProperty`  

---

## Data Sources

- Wikipedia  
- Spotify  
- MusicBrainz / Discogs (selective)  
- 22 song entries with full metadata:
  - Title, release date, artist, writer, producer, genre, label, etc.

---

## SPARQL Queries (in `Project Report`)

Includes:

- Top 3 most recent songs  
- Songs released after 2017  
- Songs by Ed Sheeran  
- Songs of genre Pop  
- A manually constructed song via SPARQL `INSERT`  
- A subgraph extraction using `CONSTRUCT`  
- Two queries using SPARQL*

---

## SHACL Validation

- Implemented in `shacl.ipynb`
- Checks:
  - Cardinality constraints  
  - Datatype restrictions  
  - Class membership

---

## Visualizations

- Created in GraphDB and Gephi from `data_model.graphml`  
- Highlights:
  - Class centrality: Songs are the most connected nodes  
  - Genre distribution: 11 genres, Pop is most represented  
  - SPARQL `CONSTRUCT`-based subgraphs (e.g., only recent Pop songs)

---

## RDF* / SPARQL* Examples

```turtle
:Xiaojing :listensTo << dbr:Easy_on_Me dbo:releaseDate "2021-10-15"^^xsd:date >> .
```

Captures listener behavior as metadata about a triple.

## Takeaways

- Semantic technologies can represent music metadata flexibly and precisely 
- Custom ontologies complement external vocabularies for personalization 
- SPARQL* and SHACL enrich graph querying and validation 
- RDF graphs provide a strong foundation for knowledge-based music apps

## Tools Used

-  RDF & Turtle via Protégé and text editors 
- GraphDB for graph storage and visualization 
- Jupyter for SHACL and SPARQL execution 
- Gephi for .graphml ontology visualization

## License

- This repository is for educational and academic use only.
- No copyrighted data.

## How to Reuse

To explore or reuse this project:

- Clone the repository 
- Open script.ipynb or shacl.ipynb in Jupyter 
- Visualize data_model.graphml in Gephi or GraphDB 
- Modify resources.ttl and classes_properties.ttl to extend the ontology