# KIP-390

## Start the environment and code compilation

```shell
    cd env
    docker compose up -d
    cd ..
    # compile the project and move to the app folder
    mvn clean package
```

Creating the needed topics and compiling the project

```shell
  # create topic
  cd env/
  docker compose exec broker1 kafka-topics --bootstrap-server broker1:9092 --create --topic crm.users
  cd ..
```

## Before KIP running

### Run producer

```shell
   cd before-kip
    java -Xrunjdwp:transport=dt_socket,address=5005,server=y,suspend=n -classpath target/before-kip-1.0.0-SNAPSHOT-jar-with-dependencies.jar com.tomasalmeida.kip.before.clients.ProducerRunner
 
```

### Run consumer

```shell
   java -Xrunjdwp:transport=dt_socket,address=5006,server=y,suspend=n -classpath target/before-kip-1.0.0-SNAPSHOT-jar-with-dependencies.jar com.tomasalmeida.kip.before.clients.ConsumerRunner

```

## After KIP running

```shell
   cd after-kip
    java -Xrunjdwp:transport=dt_socket,address=5007,server=y,suspend=n -classpath target/after-kip-1.0.0-SNAPSHOT-jar-with-dependencies.jar com.tomasalmeida.kip.after.clients.ProducerRunner
 
```

### Run consumer

```shell
   java -Xrunjdwp:transport=dt_socket,address=5008,server=y,suspend=n -classpath target/after-kip-1.0.0-SNAPSHOT-jar-with-dependencies.jar com.tomasalmeida.kip.after.clients.ConsumerRunner

```
