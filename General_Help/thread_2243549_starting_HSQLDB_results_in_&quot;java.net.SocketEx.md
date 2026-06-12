---
title: "starting HSQLDB results in &quot;java.net.SocketException: unrecognized TCP option: 4102&quot;"
date: 2014-09-09
forum: General Help
---

### Post by moe6 on 2014-09-09
Hello everyone,

I have Ubuntu Cloud 14.04 running on an instance of Openstack. The instance has 2 VCPU, 4 GB RAM and 20GB disk space. My main goal is to install openCRX, an Open Source CRM Tool. After installing openCRX I tried to run it but all I got were some errors. After some unsuccessful attempts of finding the cause I seeked for help in the openCRX Community Forum. One person tried to help me but he came to the conclusion, that it has to be a low-level Linux problem. The error comes up when I try to start HSQLDB, which is a preinstalled and configured database that comes with openCRX. 

[COLOR=#555555][FONT=sans-serif]**"./db.sh run" results in this output:**[/FONT][/COLOR][INDENT][I]ubuntu@opencrx:~/opencrx/data/hsqldb$ ./db.sh run
[Server@73e0e19d]: [Thread[main,5,main]]: checkRunning(false) entered
[Server@73e0e19d]: [Thread[main,5,main]]: checkRunning(false) exited
[Server@73e0e19d]: Startup sequence initiated from main() method
[Server@73e0e19d]: Could not load properties from file
[Server@73e0e19d]: Using cli/default properties only
[Server@73e0e19d]: Initiating startup sequence...
[Server@73e0e19d]: [Thread[HSQLDB Server @73e0e19d,5,main]]: run()/openServerSocket():
java.net.SocketException: unrecognized TCP option: 4102
at java.net.AbstractPlainSocketImpl.setOption(AbstractPlainSocketImpl.java:260)
at java.net.ServerSocket.setSoTimeout(ServerSocket.java:585)
at org.hsqldb.server.Server.openServerSocket(Unknown Source)
at org.hsqldb.server.Server.run(Unknown Source)
at org.hsqldb.server.Server.access$000(Unknown Source)
at org.hsqldb.server.Server$ServerThread.run(Unknown Source)
[Server@73e0e19d]: Initiating shutdown sequence...
[Server@73e0e19d]: Shutdown sequence completed in 151 ms.
[Server@73e0e19d]: 2014-08-28 11:22:14.886 SHUTDOWN : System.exit() is called next[/I]
[/INDENT]

I am very desperate and would be very very thankful for any input.
My whole conversation in the openCRX Forum can be found here

[http://sourceforge.net/p/opencrx/discussion/329844/thread/428ab9f6/](http://sourceforge.net/p/opencrx/discussion/329844/thread/428ab9f6/)

---

### Post by oldfred on 2014-09-10
Haven't a clue on specific hardware nor software.

But start up mentions Java. Standard install is the opensource version openjdk and most apps work with that. 
But a few need the version installed from Oracle.

Do instructions mention anything about Java version required?

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by moe6 on 2014-09-11
Yes, the openCRX tutorial says to install OpenJDK 6 JDK which I installed along with the supported Apache ANT version (1.9.4). It mentions that the version from Oracle can be installed too, but I went with the primary suggested OpenJDK. I will try to the Oracle version. To install and use Oracle Java I just have to install it with apt-get install and then change the /etc/environment path to the Oracle-path, or do I have to do any more steps?

---

### Post by oldfred on 2014-09-11
Originally Ubuntu had the Sun Java in the repositories, but soon after it became Oracle they converted to only the open version. I think you have to directly download from Oracle and make sure you do not have any conflicts.

But if they suggest that OpenJDK works then that may not be issue. But I have no idea what it may be. Or perhaps versions differences?

---

