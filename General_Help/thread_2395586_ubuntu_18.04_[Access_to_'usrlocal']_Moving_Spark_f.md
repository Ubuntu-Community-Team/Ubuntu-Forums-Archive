---
title: "ubuntu 18.04 [Access to '/usr/local']: Moving Spark from home to /usr/local"
date: 2018-07-04
forum: General Help
---

### Post by sirnewbee on 2018-07-04
Disclaimer: I'm new to linux OS

I was already able to extract Spark onto my home. But the problem really is moving it to "/usr/local".
I used [https://datawookie.netlify.com/blog/2017/07/installing-spark-on-ubuntu/](https://datawookie.netlify.com/blog/2017/07/installing-spark-on-ubuntu/) as my reference for setting up Spark.

The problem starts here:
$ sudo mv spark-2.3.1-bin-hadoop2.7 /usr/local/

   Output:
   mv: cannot move 'spark-2.3.1-bin-hadoop2.7' to '/usr/local/spark-2.3.1-bin-hadoop2.7': Directory not empty


$ sudo ln -s /usr/local/spark-2.3.1-bin-hadoop2.7/ /usr/local/spark
$ [COLOR=#999999]cd[/COLOR] /usr/local/spark

The thing is I created a text file on '/usr/local', and now I can't proceed to the next command and check if I installed Spark right.

Hoping someone could help me out.

---

### Post by yancek on 2018-07-04
I tested your mv command by creating a spark* directory with several files in it and it copied the directory with files to /usr/local so I'm not sure what the problem is, should work.

If you can't mv the spark directory to /usr/local you won't be able to create the link, at least it won't work.  Do you or did you have a Spark/spark directory in /usr/local before the mv command?  If your mv command doesn't work, you could try creating the spark directory with the with the correct name in /usr/local, then copying the files inside from your home directory with the command below:

```
mv spark-2.3.1-bin-hadoop2.7/* /usr/local/2.3.1-bin-hadoop2.7/
```

> The thing is I created a text file on '/usr/local', and now I can't proceed to the next command and check if I installed Spark right.

I don't see how creating a text file in /usr/local would have any effect on this process.  Not sure why your mv command failed.

---

