# 📊 Budgeting App Database Setup

Welcome to the database setup for the Budgeting App! Our app is designed to help you manage your finances by keeping track of your expenses and income. This guide will walk you through the process of setting up a CouchDB database using Docker, which our app relies on to store and manage data.

## 📚 Prerequisites

Before we begin, please make sure you have the following software installed:

- [Docker](https://www.docker.com/get-started) - Our app uses Docker to run the database in an isolated environment, ensuring it works the same way on every machine.

## 🚀 Getting Started

Ready to get started? Great! Just follow these steps:

1. First, clone our project repository to your machine:

   ```shell
   git clone https://github.com/resivalex/budgeting-app-couchdb.git
   ```

2. Next, navigate to the project directory:

   ```shell
   cd budgeting-app-couchdb
   ```

3. Create an `.env` file in the project directory. This file will hold some important settings for our app. Here's an example:

   ```plaintext
   COUCHDB_USER=admin
   COUCHDB_PASSWORD=password
   PORT=9002
   ```

   **Note:** Be sure to replace the values in the example with your own!

4. Have a look at the `docker-compose.yml` file. This is the recipe Docker follows to build our app. By default, it uses the `couchdb` image and exposes port `9002`. Feel free to adjust these as necessary.

5. Time to start the app! Just run:

   ```shell
   docker-compose up -d
   ```

   This will start the CouchDB service in the background.

6. Once the app is up and running, you can access it at [http://localhost:9002](http://localhost:9002). Give yourself a pat on the back - you did it!

## ⚙️ Configuration

The `docker-compose.yml` file lets you tweak a few things:

- `image`: This is the Docker image we use for the CouchDB service. By default, it's `couchdb`.
- `container_name`: This sets the name for our CouchDB container. By default, it's `budgeting-app-couchdb`.
- `env_file`: This is the path to the `.env` file that holds the settings our app needs.
- `volumes`: This tells Docker to link the `./data` directory in our project to the CouchDB container, giving us persistent data storage.
- `ports`: This maps the host port to the CouchDB container port. It uses `${PORT:-5984}` by default, meaning it will use port `5984` unless you set a `
