---
title: "problem to start tomcat"
date: 2005-10-15
forum: General Help
---

### Post by ento on 2005-10-15
When i type sh /usr/local/tomcat/bin/startup.sh i will get this meassage:
Cannot find /usr/local/tomcat/bin/catalina.sh
This file is needed to run this program

The file is there

/stefan

---

### Post by ento on 2005-10-15
solved it. some files could not be exec.

---

### Post by 45t3r15k on 2006-07-03
[QUOTE=ento]When i type sh /usr/local/tomcat/bin/startup.sh i will get this meassage:
Cannot find /usr/local/tomcat/bin/catalina.sh
This file is needed to run this program

The file is there

/stefan[/QUOTE]

In case anyone else runs into this problem, I solved it this way. I am running 6.06 and used to installing tomcat from source. 

A couple of things about Ubuntu's tomcat installation is that it runs on port 8180 by default instead of 8080. You can change this in /etc/tomcat5/server.xml. 

I had no luck with the startup and shutdown shell scripts either. To start and stop tomcat, I found that you can run /etc/init.d/tomcat5 with a start or stop argument. This is what gets run when you boot. I added a symbolic link to my $PATH to this file to make life easier during development and configuration tuning. Make sure to add $JAVA_HOME to your ~.bashrc file. It does not get put there automatically when you install a JDK or JRE. I have a couple JDKs installed via Synaptic and I set $JAVA_HOME to /usr/lib/j2se/1.4

---

### Post by Jane Shara on 2006-07-14
I think if ubuntu 6 is going to be around for 2 years it might be a good idea to make sure that getting tomcat working is not complicated, i took me many hours (as a beginner to tomcat) to get it working, you cant just install the right pacckages and start it up! At the very least their should be some helpful documentation on it, which I cant find, does anyone know of any?

---

### Post by pmasiar on 2006-12-19
your wish is fulfilled: [https://help.ubuntu.com/community/EclipseWebTools](https://help.ubuntu.com/community/EclipseWebTools) Enjoy!

---

