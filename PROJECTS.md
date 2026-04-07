# Satya Kumar - Project Portfolio

> A comprehensive overview of all projects on GitHub, spanning full-stack development, cloud engineering, AI/ML, data science, and DevOps.

---

## Table of Contents

| # | Project | Domain | Primary Language |
|---|---------|--------|-----------------|
| 1 | [Banking App - Spring Cloud Microservices](#1-banking-app---spring-cloud-microservices) | Full Stack / Microservices | Java |
| 2 | [Sentiment Analysis Web App (AWS SageMaker)](#2-sentiment-analysis-web-app-aws-sagemaker) | AI / Cloud | Python |
| 3 | [Itinerary Planner - Smart Tour Recommendations](#3-itinerary-planner---smart-tour-recommendation-system) | Full Stack | Java |
| 4 | [Real-Time Fraud Detection System](#4-real-time-fraud-detection-system) | Big Data / Stream Processing | Scala |
| 5 | [Brain Mapping EEG Classification](#5-brain-mapping-eeg-classification-system) | AI / Signal Processing | Python |
| 6 | [Spring Boot Monitoring (Prometheus & Grafana)](#6-spring-boot-monitoring-with-prometheus--grafana) | DevOps / Observability | Java |
| 7 | [Medical Insurance Cost Prediction](#7-medical-insurance-cost-prediction) | Machine Learning | Python |
| 8 | [U.S. Nursing Homes Financial Analysis](#8-us-nursing-homes-financial-analysis-20152021) | Data Analysis | Python |
| 9 | [Time Series Analysis & Forecasting](#9-time-series-analysis--forecasting-with-python) | Data Science | Python |
| 10 | [Java Chat System](#10-java-chat-system) | Networking | Java |

---

## 1. Banking App - Spring Cloud Microservices

**Repository:** [bank-app-spring-cloud-microservices](https://github.com/satyaaravapalli9-sys/bank-app-spring-cloud-microservices)
**Primary Language:** Java
**Domain:** Full Stack / Microservices Architecture

### Overview

This project demonstrates the complete architectural evolution of a banking application, progressing step-by-step from a monolithic structure to a fully distributed microservices ecosystem using the Spring Cloud framework. It serves as a hands-on reference for understanding how enterprise applications are decomposed, scaled, and made resilient using industry-standard patterns.

### Architecture Evolution (9 Stages)

| Stage | Concept | Technology Introduced |
|-------|---------|----------------------|
| **1** | Monolithic Application | Single JAR deployment |
| **2** | Microservice Decomposition | Spring Cloud — split by business functionality |
| **3** | Centralized Configuration | Spring Cloud Config Server (GitHub-backed) |
| **4** | Client-Side Load Balancing | Spring Cloud Netflix Ribbon / Spring Cloud LoadBalancer |
| **5** | Service Discovery | Netflix Eureka Server — dynamic hostname/port resolution |
| **6** | Fault Tolerance | Hystrix Circuit Breaker & Fallback patterns |
| **7** | API Gateway | Zuul — single entry point for all microservices |
| **8** | Declarative REST Clients | OpenFeign — replaces RestTemplate for inter-service calls |
| **9** | Distributed Tracing | Spring Cloud Sleuth + Zipkin — request tracing across services |

### Key Technical Concepts

- **Config Server:** All microservice configurations are stored in a central GitHub repository and served dynamically via Spring Cloud Config Server. Each microservice acts as a Config Client.
- **Service Discovery:** Netflix Eureka provides a registry for services to register themselves and discover other services dynamically, eliminating hardcoded hostnames and ports.
- **Circuit Breaker:** Hystrix monitors inter-service calls and breaks the circuit when failure thresholds are exceeded, with fallback methods providing graceful degradation.
- **API Gateway:** Zuul acts as the single point of contact for the UI, routing requests to appropriate microservices while applying cross-cutting concerns like load balancing and circuit breaking.
- **Distributed Tracing:** Sleuth injects trace IDs, span IDs, and service names into logs. Zipkin aggregates these to visualize the full request path across all microservices.

### Tech Stack

`Java` `Spring Boot` `Spring Cloud` `Netflix Eureka` `Zuul` `Hystrix` `Ribbon` `OpenFeign` `Sleuth` `Zipkin` `Maven`

---

## 2. Sentiment Analysis Web App (AWS SageMaker)

**Repository:** [sentiment-analysis-webapp-sagemaker](https://github.com/satyaaravapalli9-sys/sentiment-analysis-webapp-sagemaker)
**Primary Language:** Python (Jupyter Notebook)
**Domain:** AI / AWS Cloud

### Overview

A web application that determines the sentiment (positive or negative) of movie reviews using a machine learning model deployed on AWS SageMaker. The model is trained on the IMDB dataset and served through a serverless architecture combining Lambda, API Gateway, and SageMaker.

### Architecture

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   Web App    │────>│ API Gateway  │────>│   Lambda     │────>│  SageMaker   │
│  (Frontend)  │<────│  (REST URL)  │<────│  (Python)    │<────│  (ML Model)  │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
```

1. **Web App (Frontend):** Collects the user's movie review text input.
2. **API Gateway:** Exposes a public REST endpoint that accepts review data.
3. **AWS Lambda:** A Python function that receives data from API Gateway, forwards it to the SageMaker endpoint, and returns the prediction.
4. **AWS SageMaker:** Hosts the trained sentiment analysis model. Receives input data, performs inference, and returns positive/negative classification.

### How It Works

- User submits a movie review through the web interface
- The review text is sent to an API Gateway endpoint
- API Gateway triggers a Lambda function
- Lambda invokes the SageMaker endpoint for inference
- The model returns a sentiment prediction (Positive / Negative)
- The result is displayed back to the user in real-time

### Tech Stack

`Python` `AWS SageMaker` `AWS Lambda` `AWS API Gateway` `IMDB Dataset` `Jupyter Notebook` `HTML/CSS/JavaScript`

---

## 3. Itinerary Planner - Smart Tour Recommendation System

**Repository:** [itinerary-planner](https://github.com/satyaaravapalli9-sys/itinerary-planner)
**Primary Language:** Java
**Domain:** Full Stack Web Application

### Overview

A modern Java web application that recommends personalized tour packages based on user preferences. The entire UI is built in Java using Vaadin Flow (no separate frontend framework), with Spring Boot on the backend and MongoDB for data persistence.

### Features

- **User Authentication** — Login/logout with custom AuthService
- **Personalized Recommendations** — Tour packages filtered by user preferences
- **Trip Type Filtering** — Adventure, Relaxation, Cultural, and more
- **Preference Management** — Budget range, travel dates, accommodation type, food preferences
- **Dynamic Package Display** — Vaadin Cards with responsive layout
- **Admin Control** — Tour packages managed directly via MongoDB

### Tech Stack

| Layer | Technology |
|-------|------------|
| UI | Vaadin Flow (Java-based UI framework) |
| Backend | Spring Boot (REST-ready) |
| Database | MongoDB (NoSQL) via Spring Data |
| Styling | Custom CSS with CSS Variables |
| Authentication | Custom AuthService |
| Build Tool | Maven |
| Language | Java 17+ |

### Project Structure

```
src/main/java/org.vaadin.example/
├── model/          # Data models (UserPreferences, TourPackage)
├── repositories/   # MongoDB Repositories
├── service/        # Filtering & Auth Services
├── layout/         # MainLayout (Sidebar, Navigation)
└── views/          # UI Views (Dashboard, Preferences, etc.)
```

### Sample Data Model

```json
{
  "packageId": "goa_adventure_3d_15k",
  "destination": "Goa",
  "budgetRange": [10000, 15000],
  "tripType": "Adventure",
  "tripDuration": 3,
  "accommodation": {
    "type": "Resort",
    "budgetAllocation": 5000,
    "ratings": [3, 4],
    "amenities": ["WiFi", "Breakfast"]
  }
}
```

### Future Enhancements

- Google Maps integration for destinations
- AI-powered smart recommendations
- Custom itinerary planner with drag-and-drop

---

## 4. Real-Time Fraud Detection System

**Repository:** [real-time-fraud-detection](https://github.com/satyaaravapalli9-sys/real-time-fraud-detection)
**Primary Languages:** Scala (27K LOC), Java (11K LOC), Python (6K LOC)
**Domain:** Big Data / Stream Processing

### Overview

A real-time fraud detection pipeline that identifies fraudulent credit card transactions as they occur. The system uses stream processing to analyze transaction patterns and flag anomalies, with a dashboard for monitoring alerts and a Cassandra-backed data layer for persistence.

### System Components

| Component | Purpose | Technology |
|-----------|---------|------------|
| **Creditcard Producer** | Generates/streams credit card transaction events | Java |
| **Fraud Detection** | Core stream processing engine that analyzes transactions in real-time and classifies them as legitimate or fraudulent | Scala |
| **Fraud Alert Dashboard** | Web-based dashboard for monitoring detected fraud alerts | Java (Spring Boot) |
| **Cassandra Python** | Data persistence layer and query interface for storing/retrieving transaction records and fraud alerts | Python, Apache Cassandra |

### Architecture

```
┌───────────────────┐     ┌───────────────────┐     ┌───────────────────┐
│  Creditcard       │────>│  Fraud Detection   │────>│  Fraud Alert      │
│  Producer (Java)  │     │  Engine (Scala)    │     │  Dashboard (Java) │
└───────────────────┘     └───────────────────┘     └───────────────────┘
                                   │
                                   ▼
                          ┌───────────────────┐
                          │  Apache Cassandra  │
                          │  (Python Client)   │
                          └───────────────────┘
```

### Tech Stack

`Scala` `Java` `Python` `Apache Cassandra` `CQL` `Stream Processing` `Spring Boot` `Maven` `Shell Scripts`

---

## 5. Brain Mapping EEG Classification System

**Repository:** [brain-mapping-eeg-classification](https://github.com/satyaaravapalli9-sys/brain-mapping-eeg-classification)
**Primary Language:** Python
**Domain:** AI / Biomedical Signal Processing

### Overview

A modern Python implementation of the 2013 "Brain Mapping Using MATLAB Technology" research project. It classifies EEG (electroencephalogram) signals as **normal** or **abnormal** using **2D Discrete Wavelet Transform** through a professional Flask web application.

### How It Works

1. **Input:** User uploads an EEG spectrogram image (PNG, JPG, BMP)
2. **Preprocessing:** Image is converted to grayscale and normalized to 256x256 pixels
3. **Feature Extraction:** 3-level 2D Discrete Wavelet Transform using Daubechies `db1` wavelet
4. **Pattern Matching:** Mean Square Error (MSE) calculated against 5 reference patterns
5. **Classification:** Threshold-based decision — MSE < 600 = Normal, MSE >= 600 = Abnormal
6. **Output:** JSON response with classification, confidence score, matched frame, and MSE values

### Technical Architecture

```
Frontend (HTML5/CSS3/JS)
        │
        ▼ HTTP/REST
Flask Web Application
        │
        ▼ Function Calls
Signal Processing Engine (PyWavelets + NumPy)
        │
        ▼ File System
Reference Data Layer (Pre-computed patterns)
```

### Algorithm Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Wavelet Type | `db1` (Haar) | Orthogonal, matches original MATLAB implementation |
| Decomposition Levels | 3 | Optimal balance of detail vs. computation |
| Classification Threshold | 600 | Empirically determined from reference data |
| Image Dimensions | 256 x 256 | Standard size for consistent comparison |
| Reference Patterns | 5 | Sufficient diversity for robust matching |

### Performance

- **Processing Time:** ~2-3 seconds per image
- **Memory Usage:** ~100MB baseline + ~50MB per request
- **Accuracy:** 95%+ on synthetic test data

### API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Web interface |
| GET | `/info` | System status and config |
| POST | `/upload` | Upload and classify EEG image |
| GET | `/test_sample/<name>` | Process pre-loaded test sample |
| GET | `/generate_data` | Generate new reference patterns |

### Tech Stack

`Python 3.8+` `Flask` `NumPy` `PyWavelets` `Pillow` `Matplotlib` `SciPy` `Docker` `pytest` `GitHub Actions CI/CD`

---

## 6. Spring Boot Monitoring with Prometheus & Grafana

**Repository:** [spring-boot-prometheus-grafana](https://github.com/satyaaravapalli9-sys/spring-boot-prometheus-grafana)
**Primary Language:** Java
**Domain:** DevOps / Observability

### Overview

A monitoring setup for Spring Boot applications using Prometheus for metrics collection and Grafana for dashboard visualization. Demonstrates how to instrument a Spring Boot application with Micrometer and expose metrics to Prometheus, then visualize them in pre-built Grafana dashboards. Everything runs in Docker containers via Docker Compose.

### Architecture

```
┌──────────────────┐     ┌──────────────────┐     ┌──────────────────┐
│  Spring Boot     │────>│   Prometheus     │────>│    Grafana       │
│  Application     │     │  (Scrapes /      │     │  (Dashboard      │
│  (Micrometer)    │     │   actuator/      │     │   Visualization) │
│                  │     │   prometheus)    │     │                  │
└──────────────────┘     └──────────────────┘     └──────────────────┘
```

### Docker Compose Setup

Starts both Prometheus (port 9090) and Grafana (port 3000) containers with a single command:

```yaml
services:
  prometheus:
    image: prom/prometheus:latest
    ports: ["9090:9090"]
    volumes: ["./prometheus.yml:/etc/prometheus/prometheus.yml"]
  grafana:
    image: grafana/grafana:latest
    ports: ["3000:3000"]
```

### Prometheus Configuration

Prometheus is configured to scrape metrics from multiple Spring Boot services at the `/actuator/prometheus` endpoint. Supports monitoring of:

- Main application (port 8080)
- Admin service (port 8110)
- Discovery service (port 8100)
- Content service (port 8200)
- Frontend service (port 8201)
- Gateway service (port 8000)
- Zipkin server (port 9411)

### Grafana Dashboard

Uses the "Java Micrometer Basics" dashboard (ID: 4683) from Grafana.com, providing JVM metrics including:

- Heap and non-heap memory usage
- Garbage collection statistics
- Thread counts and states
- HTTP request metrics
- CPU usage

### Spring Boot Dependencies

```gradle
compile 'org.springframework.boot:spring-boot-starter-actuator'
compile 'io.micrometer:micrometer-spring-legacy:1.0.6'
compile 'io.micrometer:micrometer-registry-prometheus:1.0.6'
```

### Tech Stack

`Java` `Spring Boot` `Spring Actuator` `Micrometer` `Prometheus` `Grafana` `Docker` `Docker Compose` `YAML`

---

## 7. Medical Insurance Cost Prediction

**Repository:** [medical-insurance-cost-prediction](https://github.com/satyaaravapalli9-sys/medical-insurance-cost-prediction)
**Primary Language:** Python (Jupyter Notebook)
**Domain:** Machine Learning / Predictive Modeling

### Overview

A machine learning project that predicts health insurance costs based on personal attributes. Uses exploratory data analysis and multiple regression algorithms to identify the key factors influencing medical expenses, then selects the best-performing model for prediction.

### Dataset

**Source:** [Kaggle - Medical Cost Personal Dataset](https://www.kaggle.com/mirichoi0218/insurance)

| Feature | Description |
|---------|-------------|
| `age` | Age of primary beneficiary |
| `sex` | Gender (male/female) |
| `bmi` | Body Mass Index (kg/m^2) |
| `children` | Number of dependents covered |
| `smoker` | Smoking status (yes/no) |
| `region` | Residential area in the US (NE, SE, SW, NW) |
| `charges` | Individual medical costs billed (target variable) |

### Key Insights from EDA

- Most people in the dataset are non-smokers and obese
- Gender and region distributions are nearly balanced
- **Smokers with BMI above 30** have significantly higher medical costs
- **Older smokers** incur the most expensive charges
- The combination of **smoking + obesity** produces the highest average charges

### Data Processing Pipeline

1. **Missing Values:** None found
2. **Duplicates:** 1 duplicate removed
3. **Feature Engineering:** New `weight_status` column derived from BMI score
4. **Encoding:** One-hot encoding for `sex`, `region`, `weight_status`; ordinal encoding for `smoker`
5. **Train/Test Split:** Standard split for model evaluation

### Model Comparison

| Algorithm | R2 | Train Accuracy | Test Accuracy | MAE | RMSE |
|-----------|-----|----------------|---------------|-----|------|
| Linear Regression | 0.77 | 0.74 | 0.77 | 4305.20 | 6209.88 |
| Decision Tree | 0.78 | 1.00 | 0.78 | 2798.83 | 6067.50 |
| **Random Forest** | **0.78** | **0.97** | **0.86** | **2608.55** | **4841.88** |
| Ridge | 0.86 | 0.74 | 0.77 | 4311.10 | 6238.13 |

### Tech Stack

`Python` `NumPy` `Pandas` `Scikit-learn` `Matplotlib` `Seaborn` `Jupyter Notebook`

---

## 8. U.S. Nursing Homes Financial Analysis (2015–2021)

**Repository:** [nursing-home-financial-analysis](https://github.com/satyaaravapalli9-sys/nursing-home-financial-analysis)
**Primary Language:** Python
**Domain:** Data Analysis / Healthcare Finance

### Overview

Analyzes the financial performance, quality indicators, and regulatory penalties of U.S. nursing homes from 2015 to 2021 using multiple CMS (Centers for Medicare & Medicaid Services) datasets. The project places special emphasis on the **impact of COVID-19** on net income, staffing, and operational metrics across facilities of different sizes.

### Scope

- **Time Period:** 2015–2021
- **Scope:** U.S. Nursing Homes (Small, Medium, and Large facilities)
- **Data Source:** CMS Public Datasets

### Features Analyzed

- Ownership Type (For-Profit, Non-Profit, Government)
- Number of Beds (Size Category)
- Overall Rating, Staffing Rating, Health Inspection Rating
- Occupancy Rate
- COVID-19 Period Net Income vs. Pre-COVID Net Income
- Fines and Penalties
- Medicaid/Medicare Payer Mix

### Key Findings

| Finding | Detail |
|---------|--------|
| **COVID-19 Revenue Boost** | Larger facilities (>100 beds) saw up to **1,178% increase** in net income during COVID-19 |
| **Regulatory Relaxation** | Fines and penalties dropped to **zero** during 2020-2021, reflecting policy leniency |
| **Staffing Decline** | Staffing ratings declined during the pandemic, but overall quality ratings remained steady |
| **Net Income Surge** | Net income rose drastically in 2020-2021 compared to the 2015-2019 baseline |

### Project Structure

```
├── data/           # Raw and cleaned CMS datasets (2015–2021)
├── notebooks/      # EDA, regression, and visualization notebooks
├── plots/          # Generated plots and graphs
└── final report    # Summary report (BANA 620 course)
```

### Tech Stack

`Python` `Pandas` `Matplotlib` `Seaborn` `Jupyter Notebook` `CMS Public Datasets`

---

## 9. Time Series Analysis & Forecasting with Python

**Repository:** [time-series-analysis-and-forecasting-with-python](https://github.com/satyaaravapalli9-sys/time-series-analysis-and-forecasting-with-python)
**Primary Language:** Python (Jupyter Notebook)
**Domain:** Data Science / Forecasting

### Overview

A comprehensive, structured guide covering the full spectrum of time-series analysis and forecasting using Python. Progresses from foundational concepts to advanced deep learning approaches, covering classical statistical models, Facebook Prophet, and AutoML techniques. Suitable for beginners and advanced practitioners alike.

### Curriculum

#### 1. Foundations
- **Theory:** Taxonomy of time-series analysis, forecasting model selection best practices, simple/classical methods, converting time series to supervised learning problems
- **Data Visualization:** Pandas plotting, axis formatting, date formatting, gridlines, major/minor axis control

#### 2. Exploratory Data Analysis
- Time resampling (downsampling/upsampling)
- Time shifting (forward/backward)
- Rolling window mean and expanding (cumulative) mean

#### 3. Data Analysis (statsmodels)
- Hodrick-Prescott filter for trend/cyclical decomposition
- Stationarity testing (Augmented Dickey-Fuller test)
- Granger Causality tests
- Time series decomposition (additive/multiplicative)
- Exponential smoothing: Simple EWMA, Double EWMA, Holt-Winters (Triple EWMA)

#### 4. Classical Forecasting Methods
- Autocorrelation (ACF) and Partial Autocorrelation (PACF)
- AR(p), ARMA, ARIMA models
- ETS Decomposition
- SARIMA and SARIMAX (with exogenous variables)

#### 5. Deep Learning for Time Series
- **MLPs** for time series forecasting
- **LSTMs** for sequence modeling
- **CNNs** for temporal pattern extraction
- Transformers (planned)

#### 6. Facebook Prophet
- Univariate forecasting
- Multivariate forecasting with regressors

#### 7. AutoML
- Automated time series forecasting with **FLAML**

### Tech Stack

`Python` `Pandas` `NumPy` `statsmodels` `Scikit-learn` `TensorFlow/Keras` `Facebook Prophet` `FLAML` `Matplotlib` `Jupyter Notebook`

---

## 10. Java Chat System

**Repository:** [java_chat_system](https://github.com/satyaaravapalli9-sys/java_chat_system)
**Primary Language:** Java
**Domain:** Networking / Socket Programming

### Overview

A client-server chat application where two user interfaces can communicate simultaneously in real-time. Built using Java socket programming to explore network communication fundamentals and concurrent response handling.

### How It Works

1. **Server** listens for incoming connections on a specified port
2. **Client** connects to the server
3. Both parties can send and receive messages simultaneously
4. Messages are transmitted over TCP sockets

### How to Run

```bash
# Terminal 1: Start the server
java server.java

# Terminal 2: Start the client
java client.java
```

### Key Concepts Demonstrated

- **TCP Socket Programming** — Client-server communication over TCP
- **Multithreading** — Simultaneous send/receive capabilities
- **I/O Streams** — Reading from and writing to network streams
- **Network Communication** — Understanding of how data flows between processes

### Tech Stack

`Java` `TCP Sockets` `Multithreading` `I/O Streams`

---

## Technology Summary

### Languages Used Across All Projects

| Language | Projects |
|----------|----------|
| **Java** | Banking App, Itinerary Planner, Fraud Detection, Spring Boot Monitoring, Chat System |
| **Python** | Sentiment Analysis, Brain Mapping EEG, Medical Insurance, Nursing Home Analysis, Time Series |
| **Scala** | Fraud Detection (primary engine) |
| **JavaScript** | Sentiment Analysis (frontend), Brain Mapping (frontend) |

### Domains Covered

| Domain | Projects |
|--------|----------|
| **Full Stack Development** | Banking App, Itinerary Planner |
| **Cloud Engineering (AWS)** | Sentiment Analysis (SageMaker, Lambda, API Gateway) |
| **Microservices** | Banking App (Spring Cloud ecosystem) |
| **AI / Machine Learning** | Sentiment Analysis, Brain Mapping EEG, Medical Insurance |
| **Big Data / Stream Processing** | Real-Time Fraud Detection |
| **DevOps / Monitoring** | Spring Boot Prometheus & Grafana |
| **Data Analysis** | Nursing Home Financial Analysis |
| **Data Science** | Time Series Forecasting |
| **Networking** | Java Chat System |

---

**Author:** Satya Kumar
**Email:** satyaaravapalli9@gmail.com
**GitHub:** [satyaaravapalli9-sys](https://github.com/satyaaravapalli9-sys)
**LinkedIn:** [satya-kumar](https://linkedin.com/in/satya-kumar)
