---
title: "Azureus Hangs During Startup"
date: 2005-05-21
forum: General Help
---

### Post by freedomfries on 2005-05-21
Hi,

 I'm new to Ubuntu (I'm actually running Kubuntu), but I have been running Mandrake for over a year.  I'm having trouble getting Azureus working. I've installed the latest JDK (1.5.3) and I've followed the Azureus install instructions on the unofficial ubuntu guide site. Here's the output from Azureus:

Starting Azureus...
Java exec not found in PATH, starting auto-search...
Java exec found in  /usr/java/jdk1.5.0_03/bin/
Suitable java version found  [/usr/java/jdk1.5.0_03/bin/java = 1.5.0_03]
Configuring environment...
Loading Azureus:
/usr/java/jdk1.5.0_03/bin/java -Xms16m -Xmx128m -cp "/opt/azureus/Azureus2.jar:/opt/azureus/swt.jar:/opt/azureus/swt-mozilla.jar:/opt/azureus/swt-pi.jar" -Djava.library.path="/opt/azureus" -Dazureus.install.path="/opt/azureus" org.gudy.azureus2.ui.swt.Main ''

it pauses for about a minute then prints this: 

^[[BStartSocket: passing startup args to already-running Azureus java process.


Anyone have any ideas? Azureus has always worked fine for me under windows and mandrake.

Thanks.

---

### Post by freedomfries on 2005-05-21
I spoke a little to soon, here's the output after a few more minutes:

DEBUG::Sat May 21 20:49:10 EDT 2005
  java.net.ConnectException: Connection timed out
        at java.net.PlainSocketImpl.socketConnect(Native Method)
        at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:333)
        at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:195)
        at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:182)
        at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:364)
        at java.net.Socket.connect(Socket.java:507)
        at java.net.Socket.connect(Socket.java:457)
        at java.net.Socket.<init>(Socket.java:365)
        at java.net.Socket.<init>(Socket.java:178)
        at org.gudy.azureus2.ui.swt.StartSocket.<init>(StartSocket.java:44)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:75)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:98)

---

### Post by freedomfries on 2005-05-21
ha, I feel pretty stupid, but I've answered my call for help. It turns out that during my wifi configuration, I commented out the "lo" interface interfaces file. I'm not really sure what lo is all about (other than its a loop back of some sort). 

I hope this thread helps someone else :)

---

### Post by Shanachie on 2005-11-30
I can confirm this is caused because the loopback interface isn't up, it can be started like this:
```
sudo ifup lo
```
But it is supposed to be autostarted during startup.

I have compiled a kernel, because I am writing a kernel driver, and somehow the loopback interface isn't started during init anymore. With the standard ubuntu-2.6.12-9-386 kernel there's no problem.
I'm not really familiar with ubuntu/debian network-configuration, I've just switched from gentoo.
Does anybody now how this can solved?

---

