---
title: "how do I set a CLASSPATH environment in ubntu?"
date: 2005-06-29
forum: General Help
---

### Post by young on 2005-06-29
Hi there,

      I am currently trying to set up a JDBC Driver in my ubuntu (Connector/J from MySQL).  I went to the mysql site and read their manuals on how to install this software, but I am totally lost.  They do however, give me a pretty useful piece of command line: which says,

 $ setenv CLASSPATH /path/to/mysql-connector-java-[version]-bin.jar:$CLASSPATH

I already tried this command, and the terminal throws me a message : setenv is not a valid command.   

     This is what I want to do as the manual says:

Once you have extracted the distribution archive, you can install the driver by placing mysql-connector-java-[version]-bin.jar in your classpath, either by adding the FULL path to it to your CLASSPATH enviornment variable, or by directly specifying it with the commandline switch -cp when starting your JVM

How would I do this?  Your advice would be much helpful in solving this problem.  Thank you in advance.

                                                                                        Regards,

                                                                                                             Young

---

### Post by Martin Witte on 2005-06-29
Use export (setenv is csh syntax, Linux uses bash)

martin@ubuntu:~$ export BLAH=blahdiblah
martin@ubuntu:~$ echo $BLAH
blahdiblah
martin@ubuntu:~$

---

### Post by young on 2005-06-29
I just typed in the following:

export CLASSPATH /usr/java/..../...bin.jar:$CLASSPATH (i skipped the folder and file names), and I get the following:

       directories: ' : not a valid identifier

Any ideas?

---

### Post by young on 2005-06-29
Never mind, got it figured out....Thank you so much.

---

### Post by abedbajia on 2007-10-27
u figured it out plzzzz tell me where did u put the mysql connector and what the code exactlly plzzz

---

### Post by taurus on 2007-10-27
> **abedbajia said:**
> u figured it out plzzzz tell me where did u put the mysql connector and what the code exactlly plzzz

You put that in your ~/.bashrc.

```
gedit ~/.bashrc
```

---

