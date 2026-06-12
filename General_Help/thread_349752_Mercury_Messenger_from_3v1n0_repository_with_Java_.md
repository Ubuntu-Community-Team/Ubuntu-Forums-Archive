---
title: "Mercury Messenger from 3v1n0 repository with Java 6 from Edgy backports"
date: 2007-01-30
forum: General Help
---

### Post by Robvdl on 2007-01-30
Hi, I am trying to get Mercury Messenger going from the 3v1n0 repository, with Java 6 from the Edgy Backports.

I noticed here from screenshots, that people are running it on Ubuntu, so I wanted to give it a go:

[http://www.ubuntuforums.org/showthread.php?t=262603](http://www.ubuntuforums.org/showthread.php?t=262603)

The only difference is, that I am running Java 6 from the Edgy Backports repository, since it was in there, and this is a newer version than the one you build yourself from the 3v1n0 repository. I am not running Java 5 at all, or any other versions of Java, other than Java 6 from Edgy Backports.

I'm pretty confident I have Java 6 setup correctly. I have it working in Firefox/Flock/Seamonkey/Minefied (Yes, I know, that's a lot of browsers :D). I also have it working in Eclipse (I also have the Java 6 SDK installed, also from Edgy Backports), and I am running various other Java programs no problem.

I have used sudo update-alternatives and set java 6 as the default JVM as well as the default JDK (javac), I edited the file /etc/jvm and /etc/eclipse/java_home files, so Java 6 is the first JVM in the list. Basically, everything else is working no problem with Java 6, except Mercury messenger.

When I run it, it comes up with a message box:

```

Time: 11:15:22
Info: init failed

java.lang.IllegalArgumentException: Invalid initial delay: -1
   at javax.swing.Timer.setInitialDelay(Timer.java:391)
   at javax.swing.ToolTipManager.setDismissDelay(ToolTipManager.java:165)
   at org.0.6.1.7(Unknown Source)
   at org.0.6.0.3(Unknown Source)
   at org.0.6.0.main(Unknown Source)
   at com.dMSN.Main.main(Unknown Source)

```

When I run it from the command line, I get:

```

11:15:20 Mercury/1.9RC1 [20070103] starting...
11:15:20 Loading Locations...
11:15:20 Loading Global Settings...
11:15:21 Loading Splash Screen...
Warning: Cannot convert string "-b&h-luxi sans-medium-r-normal--*-140-*-*-p-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "-misc-ar pl shanheisun uni-medium-r-normal--*-*-*-*-p-*-iso10646-1" to type FontStruct
11:15:22 [5%] Welcome rob...
11:15:22 [10%] Starting Mercury 1.9RC1...
11:15:22 [12%]   Verifying classpath...
11:15:22 [14%]   Verifying library path...

```

And... the program stops execution here.

Any ideas??

---

### Post by phossal on 2007-01-30
This might help:
[http://ubuntuforums.org/archive/index.php/t-214115.html](http://ubuntuforums.org/archive/index.php/t-214115.html)

---

### Post by phossal on 2007-01-30
In addition, I'd download the "core release" directly from the main site. It's apparently self contained.

---

### Post by Robvdl on 2007-01-31
Thanks for the hints. Well, I tried to download the Core release, but the download is not currently there. I get a 404 when I go to [http://www.mercury.to/index.php?page=Downloads](http://www.mercury.to/index.php?page=Downloads) then click on Core Release (all) - torrent.

So I tried the other link mentioned in this post: [http://ubuntuforums.org/archive/index.php/t-214115.html](http://ubuntuforums.org/archive/index.php/t-214115.html) where you download the following deb [http://prdownloads.sourceforge.net/projeto-messias/mercury-messenger_1711_B11_all.deb?download](http://prdownloads.sourceforge.net/projeto-messias/mercury-messenger_1711_B11_all.deb?download)

When I started mercury, I got the same errors mentioned in that thread, so I changed the permissions of /usr/lib/mercury and /usr/lib/mercury/Mercury.lax as the instructions say.

Ran it again, it gets further this time, but fails on some missing .so files. I do have libc6 installed by the way, so I assume that (somewhere), I would need to create symbolic links, so mercury can see these libraries, but have no idea where.

```

nawk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/jvm/java-6-sun/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

```

Maybe I should wait a while, and maybe try it again when Feisty comes out, hopefully by then there might also be a newer version of mercury that might work better.

---

### Post by phossal on 2007-01-31
Normally, when I make a response, I do whatever it is I'm responding to. So, for example, I would try to install Mercury myself. I visited the downloads page earlier and got the same 404. I happen to be a fan of installing things direct. I try to avoid the package managers whenever possible, especially for Java-based things. I'll make a note to visit the site again to see if the 404 is cleared up. If you have success in the meantime, please update the thread. :)

[edit] I am not in any way trying to persuade you from using this, but it seemed to have overwhelmingly poor reviews out and about.

---

