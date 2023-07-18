# time-series-with-vector-search
An experiment of forecasting time series with vector search

## Background

The idea here is to work with just embeddings.
Embeddings are vectors that represent some object but also some semantic meaning.
If we do a similarity search on vectors, we are basically doing a search on a similarity of the meaning.
For time series, we can try to predict how a given series will evolve given other series we've seen before.
We do this by embedding a first part of the series, and storing a few of the last values.
Then we do a similarity search on the embeddings of the first part of the series, and use the stored values of the most similar series as prediction.

The only missing piece is how to embed a time series. There are models available for embedding text, images and videos.
However, a model for time series seems missing.

There is a paper called [Time2Vec](https://arxiv.org/abs/1907.05321) that proposes a model for embedding time series.
It has a few implementations, one of which I'm using. I have no insight into the correctness or quality of the model.

## Requirements

* Python 3.10 (tested with 3.10.12)
* A [Datastax Astra](https://astra.datastax.com/) database with Vector Search enabled. 
* A secure connect bundle for the database, a token json file for the database and a keyspace in the database.
* Doing `pip install -r requirements.txt` (but preferably to a dedicated venv).

## Usage

* Run `jupyter notebook` in the root of the repo.
* Open `time-series-with-vector-search.ipynb` and follow the boxes step by step.

## Credits

* [Electricity demand data set](https://huggingface.co/datasets/rajistics/electricity_demand) 
* Stock prices fetched from [Alpha Vantage](https://www.alphavantage.co/).
* Some data processing code take from [here](https://docs.pinecone.io/docs/time-series).
* Time series embeddings
  * [Time2Vec](https://arxiv.org/abs/1907.05321)
  * [Implementation](https://github.com/ojus1/Time2Vec-PyTorch)