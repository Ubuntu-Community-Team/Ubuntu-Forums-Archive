---
title: "Java applet in firefox - no keyboard access?"
date: 2007-03-24
forum: General Help
---

### Post by peterx14 on 2007-03-24
Hi all,

I just found this link:
[http://www.physics.ox.ac.uk/jpc/Demo.html](http://www.physics.ox.ac.uk/jpc/Demo.html)

from this Slash-dot article:
[http://it.slashdot.org/article.pl?sid=07/03/24/1840256](http://it.slashdot.org/article.pl?sid=07/03/24/1840256)

but whilst the Java applet does appear to load and run properly, the virtual DOS boots and I get an A:\> prompt, I can't type any commands. I've tried clicking on the Java applet to make sure it has focus, and I've kept the mouse pointer over the applet just in case keyboard focus follows the mouse or something, but it still won't work! My Java VM is (afaik) up to date:

```
$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
```

and **about-plugins** in firefox says:

```
Java(TM) Plug-in 1.5.0_08-b03

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_08

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_08 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_08 	Java 		Yes

```

Trying the same under Windows XP does work. Anyone got any ideas?

Cheers

Peter.

---

