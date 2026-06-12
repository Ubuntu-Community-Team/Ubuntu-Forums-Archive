---
title: "gCALDaemon problem"
date: 2007-06-15
forum: General Help
---

### Post by Depressed Man on 2007-06-15
So I followed the instructions on the site and I come to the finished part where I have to start the script. But here's what I get.. any ideas?

vforviktor@vendetta:~$ '/usr/local/sbin/GCALDaemon/bin/standalone-start.sh' 
log4j:ERROR Unable to init logger!
java.io.FileNotFoundException: /usr/local/sbin/GCALDaemon/bin/../log/gcal-daemon.log (Permission denied)
        at java.io.RandomAccessFile.open(Native Method)
        at java.io.RandomAccessFile.<init>(RandomAccessFile.java:212)
        at org.gcaldaemon.logger.FileChannelAppender.activateOptions(FileChannelAppender.java:130)
        at org.apache.log4j.config.PropertySetter.activate(PropertySetter.java:247)
        at org.apache.log4j.config.PropertySetter.setProperties(PropertySetter.java:123)
        at org.apache.log4j.config.PropertySetter.setProperties(PropertySetter.java:87)
        at org.apache.log4j.PropertyConfigurator.parseAppender(PropertyConfigurator.java:645)
        at org.apache.log4j.PropertyConfigurator.parseCategory(PropertyConfigurator.java:603)
        at org.apache.log4j.PropertyConfigurator.configureRootCategory(PropertyConfigurator.java:500)
        at org.apache.log4j.PropertyConfigurator.doConfigure(PropertyConfigurator.java:406)
        at org.apache.log4j.PropertyConfigurator.doConfigure(PropertyConfigurator.java:307)
        at org.apache.log4j.PropertyConfigurator.configure(PropertyConfigurator.java:315)
        at org.gcaldaemon.core.Configurator.<init>(Configurator.java:204)
        at org.gcaldaemon.standalone.Main.main(Main.java:46)
INFO  | GCALDaemon V1.0 beta 12 starting...
INFO  | RSS/ATOM feed converter enabled.
INFO  | Local time zone is GMT-05:00.
INFO  | HTTP server starting on port 9090...
INFO  | HTTP server started successfully.
INFO  | Start listening file /home/vforviktor/.evolution/calendar/local/1181850228.7944.0@vendetta/calendar.ics...
INFO  | File listener started successfully.
INFO  | LDAP server disabled.
INFO  | Gmail notifier disabled.
INFO  | Sendmail service disabled.
INFO  | Mail terminal disabled.
INFO  | HTTP server stopped.

---

### Post by ckeswani on 2007-06-16
You need to set the permission on ../log so that the user you're running as can create files there:

sudo chmod a+r ../log
sudo chmod a+x ../log

or 
sudo chmod 645 ../log

although you'll probably run into other problems when it tries to stop certain services.  I know it's bad form but I had to run as root.

---

### Post by paul.reloaded on 2007-10-11
Hello.
I have similar problem. I use Eclipse SDK and from eclipse I start Apache Tomcat. So both should run in my context. I have rwx permissions on all folder in my home (including Apache Tomcat directory). However if I try to place log in my workspace directory (or anywhere else where I have rwx rights) log4j throws:

java.io.FileNotFoundException: ../error.txt (Permission denied)

---

### Post by hardcore_Ehb on 2008-05-05
> **paul.reloaded said:**
> Hello.
I have similar problem. I use Eclipse SDK and from eclipse I start Apache Tomcat. So both should run in my context. I have rwx permissions on all folder in my home (including Apache Tomcat directory). However if I try to place log in my workspace directory (or anywhere else where I have rwx rights) log4j throws:

java.io.FileNotFoundException: ../error.txt (Permission denied)

Hi,

Have you ever solved this problem ? I am having the very same problem . Can you hook me up ?

Regards

---

