---
title: "Daemons are still starting up?"
date: 2006-10-21
forum: General Help
---

### Post by Jochus on 2006-10-21
I installed Apache using apt-get. Everything works perfect, only I want Apache to start up when I want it to start up.

So I found [here](http://ubuntuforums.org/showthread.php?t=89491) the way to stop it, but when I start up Kubuntu, it still says: "Starting apache 2.0 webserver ..."

When I'm in KDE, and I point my browser to 127.0.0.1, Apache isn't started ( which is good of course). But I can't understand why Kubuntu still wants to start up Apache.

Also, when I want to close my pc, it says: "Stopping apache 2.0 webserver ..."

Is there a way to solve this?

---

### Post by kerry_s on 2006-10-21
How about just using a Autostart script with something like->

#!/bin/sh
killall apache &
or
#!/bin/sh
/etc/init.d/apache stop &

Just stick it in your /.kde/Autostart, make sure you make it executable. Then when ever you start kde it will stop/kill what ever programs you put in there.

---

### Post by bettlebrox on 2006-10-21
Before you do anything else, check to see if Apache is really running:

ps -ef |grep -i apache

It's possible you stopped Apache from starting up, but not Apache2 (you can have both installed).

---

### Post by Jochus on 2006-10-22
This is the result:

```
jochus@bacardi ~ $ ps -ef | grep -i apache
tomcat5   4691     1  1 11:59 ?        00:00:02 /usr/lib/j2sdk1.5-sun/bin/java -Djava.awt.headless=true -Xmx128M -Djava.endorsed.dirs=/usr/share/tomcat5/common/endorsed -classpath /usr/lib/j2sdk1.5-sun/lib/tools.jar:/usr/share/tomcat5/bin/commons-launcher.jar:/usr/share/tomcat5/bin/commons-logging-api.jar:/usr/share/tomcat5/bin/jmx.jar:/usr/lib/j2sdk1.5-sun/jre//lib/jcert.jar:/usr/lib/j2sdk1.5-sun/jre//lib/jnet.jar:/usr/lib/j2sdk1.5-sun/jre//lib/jsse.jar:/usr/share/tomcat5/bin/bootstrap.jar:/usr/share/tomcat5/bin/commons-logging-api.jar -Djava.security.manager -Djava.security.policy==/var/lib/tomcat5/conf/catalina.policy -Dcatalina.base=/var/lib/tomcat5 -Dcatalina.home=/usr/share/tomcat5 -Djava.io.tmpdir=/var/lib/tomcat5/temp org.apache.catalina.startup.Bootstrap start
jochus    6026  5451  0 12:02 pts/1    00:00:00 grep -i apache

```

So, it isn't started. But still, Kubuntu says: "starting up apache 2.0 webserver ..."

---

### Post by bettlebrox on 2006-10-22
U can rename the startup script in the runlevel directory. Look in /etc/rc2.d . There should be a startup script called S00apache2 (or something like that) and just rename it to s00apache2.

---

