---
title: "Zimbra Desktop first launch failure"
date: 2014-03-25
forum: General Help
---

### Post by br1177 on 2014-03-25
Hello guys
I'm new to UBUNTU 
Im trying to instal the Zimbra desktop after executing the installation it ask if you want to exit or launch the application
if I choose launce I get the following:
 :~/Downloads/zdesktop_7_2_2_ga_b11951_linux_i686$ (process:3182): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


(process:3182): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
/home/i4sbr/zdesktop/bin/zdesktop: 271: [: Illegal number: $[1989524*1000]
JETTY_HOME     =  /opt/zimbra/zdesktop/jetty
JETTY_RUN      =  /home/i4sbr/zdesktop/log
JETTY_PID      =  /home/i4sbr/zdesktop/log/zdesktop.pid
JETTY_CONSOLE  =  /home/i4sbr/zdesktop/log/zdesktop.out
JETTY_ARGS     =  
CONFIGS        =  /home/i4sbr/zdesktop/jetty/etc/jetty.xml
JAVA_OPTIONS   =  -client -d32 -Djava.awt.headless=true -Xms32m -Xmx128m -Xss150k -XX:MinHeapFreeRatio=20 -XX:MaxHeapFreeRatio=40 -XX:NewRatio=4 -XX:TargetSurvivorRatio=70 -XX:+UseConcMarkSweepGC -DSTART='/opt/zimbra/zdesktop/jetty/etc/start.config' -Dzimbra.home='/home/i4sbr/zdesktop' -Dzimbra.config='/home/i4sbr/zdesktop/conf/localconfig.xml' -Djava.library.path='/opt/zimbra/zdesktop/jetty/../lib' -Djava.awt.headless=true -Djava.io.tmpdir='/home/i4sbr/zdesktop/data/tmp/java' -Djava.net.useSystemProxies=true -Dsun.net.inetaddr.ttl=10 -XX:HeapDumpPath='/home/i4sbr/zdesktop/heapdump/' -XX:+HeapDumpOnOutOfMemoryError -Djetty.home='/opt/zimbra/zdesktop/jetty'
JAVA           =  /opt/zimbra/zdesktop/linux/jre/bin/java
Starting Jetty: 
Stale pid file removed: /home/i4sbr/zdesktop/log/zdesktop.pid
Jetty running pid=3224

a pop up window shows up and a loading sign appears but nothing happens 
If I close it it will not start again- from shortcut made in desktop
I have downloaded the last version and running UBUNTU 13.04
any suggestions?

---

### Post by grahammechanical on 2014-03-25
I have no experience with Zimbra. I have a little experience with alternative desktops and it is my understanding that we do not load a desktop environment when another desktop environment is running. What we do is to logout and at the login screen we select the alternative desktop environment.

This is where you should be seeking help

[https://www.zimbra.com/support/](https://www.zimbra.com/support/)

regards.

---

