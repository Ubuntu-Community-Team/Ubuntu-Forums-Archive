---
title: "Package Error Installing Grails on 12.10"
date: 2013-03-16
forum: General Help
---

### Post by jcman01 on 2013-03-16
[COLOR=#000000][FONT=Arial]I am installing Grails on Ubuntu 12.10, using the instructions [here]("http://grails.org/download/ubuntu"), but an getting an error on the 3rd step, as outlines below.[/FONT][/COLOR]

[LIST]
[*]sudo add-apt-repository ppa:groovy-dev/grails
[*]sudo apt-get update
[*]**sudo apt-get install grails-ppa**
[/LIST]
[COLOR=#000000][FONT=Arial]The error I get is shown below. I have the Sun JDK installed, and **JAVA_HOME** is set, and**JAVA_HOME/bin** is on the path.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Can someone suggest things to try to resolve this?[/FONT][/COLOR]

```
/home/buck> $ sudo apt-get install grails-ppa[sudo] password for buck: 
Sorry, try again.
[sudo] password for buck: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 default-jre-headless:i386 : Depends: openjdk-7-jre-headless:i386 (>= 7~u3-2.1) but it is not going to be installed
 openjdk-7-jre:i386 : Depends: openjdk-7-jre-headless:i386 (= 7u7-2.3.2a-1ubuntu1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
/home/buck> $ java -version
java version "1.6.0_39"
Java(TM) SE Runtime Environment (build 1.6.0_39-b04)
Java HotSpot(TM) 64-Bit Server VM (build 20.14-b01, mixed mode)



```

---

### Post by dino99 on 2013-03-16
check that ppa is well set to 12.10 (and not something else)
as its the dev ppa, send the errors to the maintainer

you can also try one of the related grails ppas

---

