---
title: "Firefox freezing with Java Plugin"
date: 2006-07-24
forum: General Help
---

### Post by max_headroom on 2006-07-24
I have the Java Plugin installed in Firefox.  Visiting sites that have Java content causes firefox to freeze (stop responding) so I have to kill it.

Here is an example of a page that contains java that causes the freeze:
[http://java.sun.com/docs/books/tutorial/essential/system/misc.html](http://java.sun.com/docs/books/tutorial/essential/system/misc.html)

Initially I thought I may have installed the packages incorrectly. I have since removed and reinstalled them and that still has not fixed the issue.  I have tried installing using Automatix, Synaptic, and from the terminal with the apt-get command and the problem occurs in all cases.

Any ideas on what I can do to get this working or anything else I can look at?  Below is the information I could think to include




Here are the installed packages:
sun-java5-plugin
sun-java5-jre
sun-java5-bin

Here is the Version of Java:
```

~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

```

Here is the firefox version:
```

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.4) Gecko/20060608 Ubuntu/dapper-security Firefox/1.5.0.4

```

Here is the output from about: plugins
```

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 7.0 r63

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Java(TM) Plug-in 1.5.0_06-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_06

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
application/x-java-applet;jpi-version=1.5.0_06 	Java 		Yes
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
application/x-java-bean;jpi-version=1.5.0_06 	Java 		Yes

```

Here are the locations of the libjavaplugin_oji.so files
```

~$ locate libjavaplugin_oji.so
/var/lib/dpkg/alternatives/libjavaplugin_oji.so
/etc/alternatives/libjavaplugin_oji.so
/usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so
/usr/lib/firefox/plugins/libjavaplugin_oji.so
/usr/lib/mozilla/plugins/libjavaplugin_oji.so
/usr/lib/mozilla-snapshot/plugins/libjavaplugin_oji.so

```

And here are the link types
```

~$ locate libjavaplugin_oji.so | xargs ls -l
lrwxrwxrwx 1 root root     62 2006-06-02 20:37 /etc/alternatives/libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so
lrwxrwxrwx 1 root root     54 2006-06-02 20:37 /usr/lib/firefox/plugins/libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji_mozilla_firefox.so
-rw-r--r-- 1 root root 213016 2005-09-19 16:44 /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavaplugin_oji.so
lrwxrwxrwx 1 root root     38 2006-06-02 20:37 /usr/lib/mozilla/plugins/libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji.so
lrwxrwxrwx 1 root root     55 2006-06-02 20:37 /usr/lib/mozilla-snapshot/plugins/libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji_mozilla_snapshot.so
-rw-r--r-- 1 root root    121 2006-06-02 20:37 /var/lib/dpkg/alternatives/libjavaplugin_oji.so

```

Here are the settings for the java:
```

:~$ sudo update-alternatives --config java
Password:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
 +    3        /usr/lib/j2se/1.4/bin/java
*     4        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

```

---

### Post by turner850 on 2006-08-04
How did you get Java installed?!??!?!

---

