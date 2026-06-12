---
title: "How to suspend a process ?"
date: 2021-02-09
forum: General Help
---

### Post by suaro on 2021-02-09
Hi Experts,

I need to suspend a process from time to time in certain testing scenarios. 
By 'suspend',  I mean I do not want the target process to repsond to external calls (i.e. tcp listeners need halt, etc...). The goal is to simulate a hung process.

Typically I use:

```

kill -STOP <pid>  to halt the process

 ... and later

kill -CONT <pid> to resume it .
``` 

The above commands works for pretty much all processes.  There are a few processes where it only partially works. 

For example,  here's a process  (PID **25391 **) :

```
# ps aux | grep 25391 | grep -v grep
hive     **25391  **1.5  2.0 28248788 1347012 ?    Sl   Feb08   8:17 /usr/lib/jvm/zulu-8-azure-amd64/bin/java -Dproc_jar -Dhdp.version=4.1.2.5 -Djava.net.preferIPv4Stack=true -XX:+ExitOnOutOfMemoryError -Xloggc:/var/log/hive/hiveserverinteractive-gc-%t.log -XX:+UseG1GC -XX:+PrintGCDetails -XX:+PrintGCTimeStamps -XX:+PrintGCCause -XX:+UseGCLogFileRotation -XX:NumberOfGCLogFiles=10 -XX:GCLogFileSize=10M -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/var/log/hive/hsi_heapdump.hprof -Dhive.log.dir=/var/log/hive -Dhive.log.file=hiveserver2Interactive.log -Dhdp.version=4.1.2.5 -Xmx1024m -Dproc_hiveserver2 -Xmx24576m -Dlog4j.configurationFile=hive-log4j2.properties -Djava.util.logging.config.file=/usr/hdp/current/hive-server2/conf_llap//parquet-logging.properties -Dyarn.log.dir=/var/log/hadoop/hive -Dyarn.log.file=hadoop.log -Dyarn.home.dir=/usr/hdp/4.1.2.5/hadoop-yarn -Dyarn.root.logger=INFO,console -Djava.library.path=:/usr/hdp/4.1.2.5/hadoop/lib/native/Linux-amd64-64:/usr/hdp/current/hadoop-client/lib/native -Dhadoop.log.dir=/var/log/hadoop/hive -Dhadoop.log.file=hadoop.log -Dhadoop.home.dir=/usr/hdp/current/hadoop-client -Dhadoop.id.str=hive -Dhadoop.root.logger=INFO,console -Dhadoop.policy.file=hadoop-policy.xml -Dhadoop.security.logger=INFO,NullAppender org.apache.hadoop.util.RunJar /usr/hdp/4.1.2.5/hive/lib/hive-service-3.1.2.4.1.2.5.jar org.apache.hive.service.server.HiveServer2 --hiveconf hive.aux.jars.path=file:///usr/hdp/current/hive-server2/lib/hive-hcatalog-core.jar
```


Now, I'll issue:

```
# kill -STOP 25391
```

I know its *partially *hung, because I'm unable to run simple jcmd calls on it.  For example,  I unable to print a thread stack:

```
# su hive

$ jcmd 25391 Thread.print
25391:
```

     < hangs indefinately > 

The above is expected behavior considering I issued a -STOP on it earlier,  but the processes listener threads are still responding. 

```
# netstat -tulpn | grep **25391**
tcp        0      0 0.0.0.0:***10001           ***0.0.0.0:*               LISTEN      25391/java
tcp        0      0 0.0.0.0:10502           0.0.0.0:*               LISTEN      25391/java

```

```
# nc -vz localhost ***10001***
Connection to localhost 10001 port [tcp/*] **succeeded**!

```


When I issue a stop on almost all (any) ,  even its listener threads are hung.

I'm trying to understand what Linux command I can use to stop (halt ) all threads within a process . 

For example,  when I issue a -STOP,  I'd expect the  nc -vz localhost 10001 to return a connection refused or timeout.

Also this specific scenario is not related to Java processes.  There are other similar java deamons/processes that provide the expected responses when -STOP is issued. 

Looking for a Linux command that will completely stop a process until its continued. 

Any tips / thoughts is greatly appreciated! 



P.S.  I'm using Ubuntu 16.04 but this happens also on Ubuntu 20

---

### Post by HermanAB on 2021-02-09
Here you go:
[https://www.gnu.org/software/bash/manual/html_node/Job-Control-Basics.html](https://www.gnu.org/software/bash/manual/html_node/Job-Control-Basics.html)
[http://web.mit.edu/gnu/doc/html/features_5.html](http://web.mit.edu/gnu/doc/html/features_5.html)

---

