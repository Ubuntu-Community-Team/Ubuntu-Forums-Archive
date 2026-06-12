---
title: "[SOLVED] Java won't work since I installed Gutsy"
date: 2008-01-20
forum: General Help
---

### Post by eamann on 2008-01-20
Hello!

I cannot get Java to work since I installed Gutsy before Christmas. I have tried all sorts of solutions put forward by others but to no avail.

Basing myself on one post I checked my files and discovered that there were no Java links in either usr/lib/mozilla/plugins or usr/lib/firefox/plugins. There was however a link in usr/lib/mozilla but it reads libjavaplugin_oji.so 

Can someone tell me how do I install the links? What do I do with ibjavaplugin_oji.so ? Move it into the firefox/plugins directory?

When I go to etc/alternatives, I find a whole batch of links to Java. Can someone please tell me whether they are OK or not? Perhaps there are too many and they contradict each other. Shoud I choose one approach  (Java, Icedtea, GCJ...) and delete all the others? 

Furthermore, when I browse the file with Nautilus I see that the firefox link is broken:
/etc/alternatives/firefox-javaplugin.so 35 bytes (link broken) 
Is that perhaps the origin of my problems. If so, how do I repair the link? I'm still fairly new to Ubuntu and would appreciate step by step instructions!

Here are the Java-related links in etc/alternatives:

firefox-javaplugin.so -> /usr/lib/gcj-4.2/libgcjwebplugin.so

lrwxrwxrwx 1 root root 35 2007-12-21 23:00 iceape-javaplugin.so -> /usr/lib/gcj-4.2/libgcjwebplugin.so

lrwxrwxrwx 1 root root 35 2007-12-21 23:00 iceweasel-javaplugin.so -> /usr/lib/gcj-4.2/libgcjwebplugin.so

lrwxrwxrwx 1 root root 36 2008-01-02 10:08 java -> /usr/lib/jvm/java-6-sun/jre/bin/java

lrwxrwxrwx 1 root root 46 2008-01-02 10:08 java.1.gz -> /usr/lib/jvm/java-6-sun/jre/man/man1/java.1.gz

lrwxrwxrwx 1 root root 24 2007-12-22 22:40 javac -> /usr/bin/gcj-wrapper-4.2

lrwxrwxrwx 1 root root 40 2007-12-22 22:40 javac.1.gz -> /usr/share/man/man1/gcj-wrapper-4.2.1.gz

lrwxrwxrwx 1 root root 19 2007-12-22 22:40 javah -> /usr/bin/gjavah-4.2

lrwxrwxrwx 1 root root 35 2007-12-22 22:40 javah.1.gz -> /usr/share/man/man1/gjavah-4.2.1.gz

lrwxrwxrwx 1 root root 39 2007-12-22 22:48 java_vm -> /usr/lib/jvm/java-6-sun/jre/bin/java_vm

lrwxrwxrwx 1 root root 28 2008-01-10 17:50 javaws -> /usr/lib/j2se/1.4/bin/javaws

lrwxrwxrwx 1 root root 38 2008-01-10 17:50 javaws.1.gz -> /usr/share/man/man1/javaws.j2se14.1.gz

lrwxrwxrwx 1 root root 41 2008-01-10 17:50 javaws.ja.1.gz -> /usr/share/man/ja/man1/javaws.j2se14.1.gz

lrwxrwxrwx 1 root root 40 2007-12-22 22:48 jcontrol -> /usr/lib/jvm/java-6-sun/jre/bin/jcontrol

lrwxrwxrwx 1 root root 43 2007-12-28 21:39 keytool -> /usr/lib/jvm/java-7-icedtea/jre/bin/keytool

lrwxrwxrwx 1 root root 62 2008-01-10 17:50 libjavaplugin_oji_mozilla_firefox.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavap lugin_oji.so

lrwxrwxrwx 1 root root 62 2008-01-10 17:50 libjavaplugin_oji_mozilla_snapshot.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavap lugin_oji.so

lrwxrwxrwx 1 root root 62 2008-01-10 17:50 libjavaplugin_oji.so -> /usr/lib/j2se/1.4/jre/plugin/i386/mozilla/libjavap lugin_oji.so

lrwxrwxrwx 1 root root 35 2007-12-21 23:00 midbrowser-javaplugin.so -> /usr/lib/gcj-4.2/libgcjwebplugin.so

lrwxrwxrwx 1 root root 35 2007-12-21 23:00 mozilla-javaplugin.so -> /usr/lib/gcj-4.2/libgcjwebplugin.so

lrwxrwxrwx 1 root root 40 2007-12-28 21:39 orbd -> /usr/lib/jvm/java-7-icedtea/jre/bin/orbd

lrwxrwxrwx 1 root root 43 2007-12-28 21:39 pack200 -> /usr/lib/jvm/java-7-icedtea/jre/bin/pack200

lrwxrwxrwx 1 root root 54 2007-12-28 21:39 pluginappletviewer -> /usr/lib/jvm/java-7-icedtea/jre/bin/pluginappletviewer

lrwxrwxrwx 1 root root 46 2007-12-28 21:39 policytool -> /usr/lib/jvm/java-7-icedtea/jre/bin/policytool

Looking forward to a reply which will help me solve this problem at last!

Eamann

---

### Post by ThrobbingBrain66 on 2008-01-20
To install Sun Java 6, use the following command in a terminal. It should solve all of your problems.

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by eamann on 2008-01-20
Thanks for your suggestion Throbbing Brain, but unfortunately it doesn't seem to work. Still no Java plugins in about:plugins and when I go to a site requiring java I still get a request to download the Java Sun plugin.

Do you know if Icedtea and Sun Java conflict with one another? Should I uninstall one or the other?

Any help appreciated!

Eamann

---

### Post by erfahren on 2008-01-20
have you tried ...
```

sudo update-alternatives --config java

```
you should see something like this - select the "sun" one if it isn't selected:
```

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:

```

do you have the gcjwebplugin installed? uninstall it if you have.

if you still have problems post the output of 
```

java -version

```
```

ls /usr/lib/firefox/plugins

```

---

### Post by eamann on 2008-01-21
Thank you Erfahren for trying to help!

In the meantime I deleted all GCJ, Icedtea and Mplayer files from my computer. This then is what I get when I do "configure Java":

eamann@Dell:~$ sudo update-alternatives --config java

[sudo] password for eamann:



There is only 1 program which provides java

(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.


And Java -version:

java version "1.6.0_03"

Java(TM) SE Runtime Environment (build 1.6.0_03-b05)

Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)


When I do ls /usr/lib/firefox/plugins
 all I get is:

libunixprintplugin.so


Why is Java not installing the plugins for Firefox?

Looking forward to hearing from you (and anyone else who thinks they can help)

---

### Post by erfahren on 2008-01-21
I went back and tracked down this thread that may be helpful [http://ubuntuforums.org/showthread.php?t=648117](http://ubuntuforums.org/showthread.php?t=648117)

---

### Post by eamann on 2008-01-22
Halleluja! Glory to God! Solved at last!

Thank you Erfahren for putting me on the right track! I have spent hours and hours browsing the forums but I do not remember having seen the post that you pointed me to. In any case I discovered there the command I needed to install the plugin:

sudo update-java-alternatives -s $(update-java-alternatives -l | cut -d' ' -f1)

Now everything works as it should.

Just to recap for the benefit of someone looking for a solution:


I installed Sun Java 6 (see instructions in previous posts)
I uninstalled Icedtea and GCJ.
I then entered the update command in the box above.
Et voilà, it worked!

Thanks once again to you Erfahren and to all the others who have tried to help me over the past weeks! That was a good experience - :) !

---

