## Introduction
To start an HDFS/Spark Workbench:
```
    docker-compose up -d
```

Spark notebook may not work so try this command.
```
docker-compose -f docker-compose-hive.yml up -d spark-notebook
```

## Interfaces

* Namenode: http://localhost:50070
* Datanode: http://localhost:50075
* Spark-master: http://localhost:8080
* Spark-notebook: http://localhost:9001
* Hue (HDFS Filebrowser): http://localhost:8088/home

## You can try this Scala example in your Spark notebook
```
import org.apache.spark.{SparkConf, SparkContext}

val config = new SparkConf().setMaster("spark://spark-master:7077").setAppName("SparkWriteApplication")
val sc = new SparkContext(config)

val numbersRdd = sc.parallelize((1 to 100).toList)
numbersRdd.saveAsTextFile("hdfs://namenode:8020/tmp/numbers-as-text")
```

