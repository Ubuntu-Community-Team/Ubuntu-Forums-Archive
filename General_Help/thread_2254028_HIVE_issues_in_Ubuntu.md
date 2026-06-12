---
title: "HIVE issues in Ubuntu"
date: 2014-11-24
forum: General Help
---

### Post by Shamik_Biswas on 2014-11-24
Hi,

I have installed Hive 0.9.0 on Hadoop 1.0.3 in Ubuntu. I have done all the necessary setup and all...
...now I am trying to start Hive and use the folliwng commands :

hduser@shamik-HP-Pavilion-g6-Notebook-PC:/usr/local/hive-0.9.0-bin/bin$ [COLOR=#ff0000]./hive[/COLOR]
WARNING: org.apache.hadoop.metrics.jvm.EventCounter is deprecated. Please use org.apache.hadoop.log.metrics.EventCounter in all the log4j.properties files.
Logging initialized using configuration in jar:file:/usr/local/hive-0.9.0-bin/lib/hive-common-0.9.0.jar!/hive-log4j.properties
Hive history file=/tmp/hduser/hive_job_log_hduser_201411242240_1688351607.txt

[COLOR=#ff0000]hive> create database emp;[/COLOR]
2014-11-24 17:11:08.051 GMT Thread[main,5,main] java.io.FileNotFoundException: [COLOR=#ff0000]derby.log (Permission denied)[/COLOR]
2014-11-24 17:11:08.149 GMT Thread[main,5,main] Cleanup action starting
ERROR XBM0H: [COLOR=#ff0000]Directory /usr/local/hive-0.9.0-bin/bin/metastore_db cannot be created.[/COLOR]

[COLOR=#ff0000]hive> show databases;[/COLOR]
2014-11-24 16:55:01.170 GMT Thread[main,5,main] Cleanup action starting
ERROR XBM0H: [COLOR=#ff0000]Directory /usr/local/hive-0.9.0-bin/bin/metastore_db cannot be created.[/COLOR]

[I][B]As you can see, I got the above errors. Please guide/suggest how to get rid of these errors...!!!

Advanced thanks[/B][/I]

---

### Post by nerdtron on 2014-11-24
Permissions issues. Hive needs read and write on it's own folders.

```
 sudo chown -R hive:hive /usr/local/hive-0.9.0-bin
ll -ah /usr/local/hive-0.9.0-bin
```

Then try the hive commands again.

---

### Post by Shamik_Biswas on 2014-11-27
thankxx a ton....that solution WORKED ... :D :D :D

---

