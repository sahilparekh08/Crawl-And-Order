# Crawl-And-Order

CIS 5550: Internet and Web Systems, University of Pennsylvania, Fall 2024

# Description

**Crawl and Order** is a scalable, cloud-based search engine. The system is designed to efficiently handle user queries
and deliver relevant search results. It consists of four major components:

1. **Crawler**: Crawls the web and fetches pages. <br />
2. **Indexer**: Builds an inverted index from the crawled pages. <br />
3. **PageRank**: Ranks pages based on their importance. <br />
4. **Ranker**: Queries the inverted index and the pagerank results to compute a final score for every relevant URL and order them in decreasing order of relevance. <br />
5. **Frontend**: Provides a user-friendly interface to perform web search and image search. <br />

Under the hood, the project is built on a scalable distributed Key-Value storage which exposes simple operation like GET, PUT and DELETE. To interact with the KV store is a distributed computational framework called Flame, which is similar in its functionality to Apache Spark.

One can submit a Job (such as a Crawler) to the Flame coordinator, which will then distribute the job to multiple workers. The workers will then fetch the data from the KV store, process it according to the functions and lambdas specified by the job and write the results back to the KV store. The KV store is also responsible for storing the intermediate results of the computation.

The most fundamental nit of computation of the Flame framework are FlameRDDs and FlamePairRDDs. The framework also exposes functions on these RDDs such as map, mapToPair, flatMap, flatMapToPair, foldByKey, filter, join, etc. which can be used to perform complex distributed computations.

Communication between the components is done using the HTTP protocol. All the components run a multithreaded HTTP webserver to listen for incoming requests. The KV Store stores data using Protobuf serialization and deserialization.

# Information

This repository only contains images in compliance with course policies that prevent publishing code to adhere with the academic integrity requirements.

The private repo [CIS-5050-PennCloud](https://github.com/sahilparekh08/CIS-5550-CrawlAndOrder) contains all the code. Please [reach out to me](mailto:sahilparekh08@gmail.com) for access.

This project has been tested on Java 21 and 22.

Notable libraries used:

1. [Protobuf](https://protobuf.dev/downloads/) : For serialization and deserialization of data.
2. [Apache Lucene](https://lucene.apache.org/core/downloads.html) : For text stemming and tokenization to build an inverted index.
3. [Apache Commons](https://commons.apache.org/downloads/index.html) (commons-lang, commons-text) : For String utility functions.
4. [Jackson](https://github.com/FasterXML/jackson-core) (annotation, core, databind) : For JSON serialization and deserialization.
5. [JSoup](https://jsoup.org/download) : For parsing HTML pages.
6. [log4j](https://logging.apache.org/log4j/2.x/download.html) : For logging.

# Diagrams

### System Architecture

![System Architecture](images/arch.jpg)

### High-Level Approach

![High Level Approach](images/high_level_approach.png)

# Team Members

[Sahil Parekh](https://www.linkedin.com/in/parekh-sahil/)

[Ashwin Alaparthi](https://www.linkedin.com/in/ashwinalaparthi/)

[Samarth Chandrawat](https://www.linkedin.com/in/samarthchandrawat/)

[Peici Qiu](https://www.linkedin.com/in/peici-qiu/)
