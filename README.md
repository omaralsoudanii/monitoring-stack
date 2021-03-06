# TIG Stack


A stack of services to enable observability for your apps powered by

- [Grafana](https://grafana.com/)
- [InfluxDB](https://www.influxdata.com/products/influxdb/)
- [Telegraf](https://www.influxdata.com/time-series-platform/telegraf/)
- [Docker](https://www.docker.com/)

## Compatibility

The stack is built via docker so it should run out of the box (it should...)

## Running Locally
- Clone the repo

    ```bash
    $ git clone https://github.com/omaralsoudanii/monitoring-stack
    ```

- Create a `.env.grafana` file similar to [`.env.grafana.example`](https://github.com/omaralsoudanii/monitoring-stack/blob/main/.env.grafana.example)

- Create a `.env.influx` file similar to [`.env.influx.example`](https://github.com/omaralsoudanii/monitoring-stack/blob/main/.env.influx.example)

- You could use [Docker Buildx](https://docs.docker.com/buildx/working-with-buildx/) as well.
Read the docs first, so you don't complain about how I ruined your environment, personally I use it with the assumption that it might crash something for me some day (hopefully, which is the perfect excuse to rebuild your machine with KDE)

- Run
  
  ```bash 
  $ docker-compose up --build -d
  ```

- Verify all the 3 containers are working
  
  ```bash
  $ docker ps
  ```
- Go to Graphana Front-end [http://localhost:3000](http://localhost:3000)
- Add a new data source **InfluxDB**
- Create dashboards, enable plugins, and **telegraf** output & input modules based on your needs
- This is a simple dashboard with the default configs

![TIG Stack](https://user-images.githubusercontent.com/7079173/130809122-9a14787b-6a92-4a6c-b36e-cfb81d6409f7.png)

## Note

Usually the way this is done is that you install InfluxDb and Grafana on 1 server, and telegraf acts as agent on other servers (the want we want to get data from),
however this repo is for demonstration purpose, you can remove telegraf from the setup and install it individually (in automated fashion) on your cluster of servers.

For production it's obvious that you should change some of the configs (certs, authentication methods) and add a reverse proxy to serve the stack (I recommend HAProxy).

