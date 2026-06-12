---
title: "java process hogging net speed"
date: 2014-12-01
forum: General Help
---

### Post by AudioFlux on 2014-12-01
This has been happening for a couple of weeks. I thought the problem was with the ISP, but that is not the case. A few days ago, out of curiosity I stopped the java process from system monitor, and my net speed returned to normal. I am certain the java process is what's using up so much of my bandwidth. Stopping it is a temporary solution as I have to do it every time I switch on my computer. I hope there is a better solution to this.

I had posted this on askubuntu before coming here. [http://askubuntu.com/q/554864/99908](http://askubuntu.com/q/554864/99908)

Here are a few details
```
root@saurabh-ubuntu:/home/saurabh# ps aux | grep java
tomcat7   1546  0.2  1.4 1915288 44708 ?       Sl   12:05   0:11 /usr/lib/jvm/default-java/bin/java -Djava.util.logging.config.file=/var/lib/tomcat7/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.awt.headless=true -Xmx128m -XX:+UseConcMarkSweepGC -Djava.endorsed.dirs=/usr/share/tomcat7/endorsed -classpath /usr/share/tomcat7/bin/bootstrap.jar:/usr/share/tomcat7/bin/tomcat-juli.jar -Dcatalina.base=/var/lib/tomcat7 -Dcatalina.home=/usr/share/tomcat7 -Djava.io.tmpdir=/tmp/tomcat7-tomcat7-tmp org.apache.catalina.startup.Bootstrap start
saurabh  14757  222 23.2 3481076 700356 ?      SNl  13:19   6:09 /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java -Dnetworkaddress.cache.ttl=0 -Dnetworkaddress.cache.negative.ttl=0 -Djava.net.preferIPv4Stack=true -Xms60m -Xmx512m -Djava.library.path=lib -classpath wrapper.jar:bcprov-jdk15on-151.jar:freenet-ext.jar:freenet.jar -Dwrapper.key=liPhWRMzGh3wcYvE -Dwrapper.backend=pipe -Dwrapper.disable_console_input=TRUE -Dwrapper.pid=1298 -Dwrapper.version=3.5.20 -Dwrapper.native_library=wrapper -Dwrapper.arch=x86 -Dwrapper.ignore_signals=TRUE -Dwrapper.service=TRUE -Dwrapper.cpu.timeout=10 -Dwrapper.jvmid=3 freenet.node.NodeStarter freenet.ini
root     16561  0.0  0.0  16896   928 pts/1    S+   13:22   0:00 grep --color=auto java
```

---

### Post by AudioFlux on 2014-12-01
Looks like Freenet was causing the problem.
This [thread]("http://ubuntuforums.org/showthread.php?t=792676") confirms that.
Uninstalled it, and the process did not show up once I killed it.
Solved.

---

