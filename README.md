# Sentiment-Driven-Market-Analysis

"This project demonstrates the ability to architect complex data systems where data doesn't just sit in a database, but flows through a 'live' environment. It highlights expertise in distributed computing, real-time event processing, and deploying Deep Learning models at scale."

Project Architecture
The system is built as a distributed pipeline consisting of four major layers:

Data Ingestion (Apache Kafka): * Simulates two live feeds: a Market Ticker (Prices/Volume) and a News Feed (Headlines).

Uses a Python-based producer to stream asynchronous events into Kafka topics.

State Detection (Hidden Markov Model):

Analyzes market volatility and returns to identify "Market Regimes" (e.g., Bull, Bear, or Neutral) using hmmlearn.

Predictive Analytics (LSTM - Deep Learning):

A Long Short-Term Memory (LSTM) recurrent neural network trained to forecast the next-step closing price based on a 20-period sliding window.

Stream Processing (Spark Structured Streaming):

The "Engine" that joins the price and news streams in real-time.

Performs Temporal Joins (matching news to prices by timestamp).

Executes real-time inference by running the LSTM model inside a Spark UDF.

Tech Stack
Engine: Apache Spark 3.5.0 (Structured Streaming)

Broker: Apache Kafka 3.6.0

Models: TensorFlow/Keras (LSTM), hmmlearn (HMM), Scikit-Learn

Language: Python 3.10+

Infrastructure: Java 8 (OpenJDK), Spark-SQL-Kafka Connectors

Key Features
Multi-Stream Joins: Correlates ticker data with external sentiment signals on the fly.

Real-Time Inference: High-frequency price prediction using Deep Learning within the streaming micro-batches.

Sentiment-Aware Logic: Adjusts financial forecasts based on the "emotional" score of incoming news headlines.

Live Dashboarding: Real-time visualization of Actual Price vs. Predicted Price vs. Moving Averages.

How to Run
1. Prerequisites
A Google Colab environment or a Linux-based machine.

The data.csv file (Financial time-series data).

2. Setup & Execution
The project is designed to be self-contained. Simply run the provided Jupyter/Colab notebook. It will automatically:

Install the required Java and Spark binaries.

Spin up a local Kafka Broker and Zookeeper instance.

Download necessary JAR connectors for Spark-Kafka integration.

Train the ML models on historical data.

Start the live streaming dashboard.

Visualizations
The pipeline produces a live-updating chart showing:

Blue Line: Actual Market Price (Live Feed).

Orange Dashed Line: LSTM Predicted Price (AI Forecast).

Green Line: 5-Period Simple Moving Average (Technical Indicator).

Repository Structure
Plaintext
├── Market_Intelligence_Pipeline.ipynb  # Main End-to-End Pipeline
├── data.csv                             # Historical Market Dataset
├── README.md                            # Project Documentation
└── zookeeper.log / kafka.log            # Service logs (generated during run)
