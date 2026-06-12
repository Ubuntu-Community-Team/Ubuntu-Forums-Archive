---
title: "Greenstone in Ubuntu Server Dapper"
date: 2007-06-30
forum: General Help
---

### Post by yacine on 2007-06-30
I am trying to install[ Greenstone, a suite of software for building and distributing digital library collections]("http://www.greenstone.org/"), on Ubuntu Server 6.06. I would appreciate any help to get it up and running.
Here are the problems encountered:
The installation went smoothly until I start running the file gli.sh. Then I get the following message: 
```
/usr/local/gsdl/gli# sh gli.sh

Greenstone Librarian Interface (GLI)
Copyright (C) 2006, New Zealand Digital Library Project, University Of Waikato
GLI comes with ABSOLUTELY NO WARRANTY; for details see LICENSE.txt
This is free software, and you are welcome to redistribute it

Checking GSDL: /usr/local/gsdl
Your environment has successfully been set up to run Greenstone
Checking Perl: /usr/bin/perl
Checking Java: /usr/bin/java

Running the Greenstone Librarian Interface...
Version: v2.73

Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$000(Unknown Source)
        at sun.awt.X11GraphicsEnvironment$1.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(Unknown Source)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(Unknown Source)
        at sun.awt.X11.XToolkit.<clinit>(Unknown Source)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at java.awt.Toolkit$2.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.getDefaultToolkit(Unknown Source)
        at javax.swing.ImageIcon.<init>(Unknown Source)
        at javax.swing.ImageIcon.<init>(Unknown Source)
        at org.greenstone.gatherer.util.JarTools.getImage(JarTools.java:93)
        at org.greenstone.gatherer.util.JarTools.getImage(JarTools.java:86)
        at org.greenstone.gatherer.util.JarTools.initialise(JarTools.java:46)
        at org.greenstone.gatherer.Gatherer.<init>(Gatherer.java:140)
        at org.greenstone.gatherer.GathererProg.main(GathererProg.java:77)
Done!

```
I looked for some help around, and I changed the Java alternatives... None of them worked. 
```
update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/jvm/java-6-sun/jre/bin/java
*     4        /usr/lib/j2re1.5-sun/bin/java

```
Also, I changed the DISPLAY 
```
export DISPLAY=localhost:10.0
```
and 
```
export DISPLAY=a3:0.0
```
It did not help either!
Also I tried changing javapath in gli.sh to point more precisely to one of the 4 alternatives, for example:
```
## ---- Check Java exists ----
javapath=/usr/lib/j2re1.5-sun/bin/java


```
I still get the same error message.

Thanks in advance

---

### Post by vikasrawal on 2007-07-24
I have been trying to install Greenstone on Ubuntu Feisty with little success. I could install Greenstone from provided binaries but gli does not work. I understand that it is because binaries are compiled using Java 1.4. I am also unable to compile the sources provide so it could use Java 6 installed on my system.

Any advice will be greatly appreciated. I am also of course trying to get help from the greenstone-users list. But may be somebody has experience of installing it on ubuntu (or has .deb packages to offer!!)!!

Vikas

---

