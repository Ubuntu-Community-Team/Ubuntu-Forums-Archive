---
title: "Cannot run Spark 2.6.3 on Ubuntu 12.04"
date: 2014-01-23
forum: General Help
---

### Post by Flame_Phoenix on 2014-01-23
I am trying to install [Spark IM]([http://www.igniterealtime.org/downloads/index.jsp](http://www.igniterealtime.org/downloads/index.jsp)) in my fresh install of Ubuntu 12.04, however I am running into all kinds of problems. The steps I have taken so far were:

1. Download the tar.gz file from the website
2. Unpack it into my Desktop
3. `sudo mv Desktop/Spark/ /opt/`

Then I try to run the file as root `sudo sh /opt/Spark/Spark`, but I get the following error:

```
    /opt/Spark/Spark: 150: /opt/Spark/Spark: bin/unpack200: not found
    Error unpacking jar files. Aborting.
    You might need administrative priviledges for this operation.
```

Since I was running the file as root (using admin) I do not understand why it says that "might need" administrative privileges ...

Here is the output of running `ls -Al`:

```
    total 56
    drwxr-xr-x 2 pedro pedro 4096 Jul  1  2011 bin
    drwxr-xr-x 4 pedro pedro 4096 Jul  1  2011 documentation
    drwxr-xr-x 2 pedro pedro 4096 Jan 23 14:28 .install4j
    drwxr-xr-x 4 pedro pedro 4096 Jul  1  2011 jre
    drwxr-xr-x 6 pedro pedro 4096 Jul  1  2011 lib
    drwxr-xr-x 2 pedro pedro 4096 Jul  1  2011 logs
    drwxr-xr-x 2 pedro pedro 4096 Jul  1  2011 plugins
    drwxr-xr-x 3 pedro pedro 4096 Jul  1  2011 resources
    -rwxr-xr-x 1 pedro pedro 8528 Jul  1  2011 Spark
    -rwxr-xr-x 1 pedro pedro 7520 Jul  1  2011 starter
    drwxr-xr-x 3 pedro pedro 4096 Jul  1  2011 xtra
```

The file I am trying to run is a "sh" file, so I do not need to do `sudo chmod +x Spark` right?

Why is this not running? What do I need to do to fix it?

---

### Post by Flame_Phoenix on 2014-01-23
Solution to this problem can be found here:

[http://askubuntu.com/questions/409658/cannot-run-spark-2-6-3-on-ubuntu-12-04/409686#409686](http://askubuntu.com/questions/409658/cannot-run-spark-2-6-3-on-ubuntu-12-04/409686#409686)

---

