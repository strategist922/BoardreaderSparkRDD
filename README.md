# BoardreaderSparkRDD
<u>Custom SparkRDD to read Boardreader REST APIs</u>


Parameters of the RDD are as follows:

  ```BoardreaderRDD(sc: SparkContext, url: String, numPartitions: Int, mapRow: (T) => String)```

Where url corresponds to the Boardreader REST API

RDD Usage:
Copy the jar file https://github.com/Effyis/BoardreaderSparkRDD/tree/master/target/boardreader-spark-rdd-project-0.0.1-SNAPSHOT-jar-with-dependencies.jar.

To use with Spark Scala shell, refer the above jar file location while invoking the Spark Scala Shell

 ```./spark-shell --jars /<jar location>//boardreader-spark-rdd-project-0.0.1-SNAPSHOT-jar-with-dependencies.jar```
<br><br>Invoke BoardreaderRDD by passing the Boardreader API URL

```import boardreader.spark.rdd._ ```

```val data = new BoardreaderRDD(sc, "http://api.boardreader.com/v1/Boards/Search?&offset=0&query=trump&filter_date_from=1459828800&filter_date_to=1467911528&sort_mode=default&filter_language=English&body=snippet&key=boardreaderkey&rt=json",  numPartitions = 1, mapRow = {x=>x.asInstanceOf[String]})```

```println(data.collect().toList)```
