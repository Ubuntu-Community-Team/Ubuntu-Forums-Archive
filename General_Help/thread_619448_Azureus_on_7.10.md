---
title: "Azureus on 7.10"
date: 2007-11-21
forum: General Help
---

### Post by TKDWILSON on 2007-11-21
I am a complete beginner to ubuntu but want to switch over completely from windows.  I can not get azureus to start up at all in ubuntu 7.10.  I type azureus in the command line and get this:  

ubuntu@ubuntu:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/eclipse/swt/widgets/Display (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

Can anyone please help me making it as simple as possible?  What do I need to type in the command line to fix it?  Is there something I can uninstall it fix it?  

Also, I had azureus working on another machine and I couldn't see where to install addons like you can with windows.  I really miss the speed scheduler and the safe peer plugins. 

Please help if you can.  I really don't know what all that above means, and I use azureus a lot so it is not something that can be replaced for me.  Thank you so much.  

Eric Wilson
[email]TKDWILSON@GMAIL.COM[/email]

---

### Post by por100pre1 on 2007-11-21
I see Azureus issues posted here almost everyday! Try using Deluge. Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo apt-get install deluge-torrent
```

**BTW, Please remove your email address, otherwise it will be prey of spam bots!**

---

### Post by TKDWILSON on 2007-11-21
I will give it a try, but I would like to get azureus working.  Or Vuze.  Or Bittyrant.  Something that looks like Azureus that I am familiar with.

---

### Post by NineseveN on 2007-11-21
I installed Azureus via the Add/Remove programs (or was it Auotmatix2? I forget) and then just click the icon in the programs menu to start it. Works wondefully in 7.10.

I don't really know jack, but is it possible the install was bad? Can you remove and retry the install?

---

### Post by fish2ways on 2007-11-21
Hi
I can't pretend to clearly understand the info you provide but I would guess it may be a Java problem.
All I can say is I'm using Gutsy and Azureus without any problems. 
Hope you get it sorted.

---

### Post by Ocxic on 2007-11-21
"sudo configure-alternatives --config java" and select another java version,, untill it works,, ussually it's just an error in azureus,,, and you'll prolly be able to change back to the original one u were using,, after a start and restart od azureus.

---

### Post by Pyrophorus on 2007-11-21
> **por100pre1 said:**
> I see Azureus issues posted here almost everyday! Try using Deluge. Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo apt-get install deluge-torrent
```



```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deluge-torrent
pyrophorus@pyrophorus:~$ 
pyrophorus@pyrophorus:~$

```

was my result

---

### Post by TKDWILSON on 2007-11-21
I just used add remove for that.  I really want to get azureus working though.  I miss being able to pause torrents when fished downloading so I can seed later, and I miss the graphical interface.  The viewing of the files before they are downloaded.  The safe peer plugin, etc.  That looks like a nice client, I just want to get my own working though.

---

### Post by TKDWILSON on 2007-11-21
I already suspect it is a Java problem, but I have no idea how to fix it.  I don't even know how to purge my computer of java and reinstall it.  Add Remove will not let you and Symantic I cant find everything I need.

---

### Post by TKDWILSON on 2007-11-21
This appears to be the error, I just don't know what it means or what to do with it.  

.UnsupportedClassVersionError: org/eclipse/swt/widgets/Display (Unsupported major.minor version 49.0

---

### Post by JBAlaska on 2007-11-21
You can have more than one version of java installed, and that messes azureus up
Do a:
```
java -version
```

If you have more that one java, do;
```
sudo update-alternatives --config java
```

And choose another version, I think 5 is good for azureus.

If you don't have java, do;
```
sudo apt-get install sun-java5-jre
```

You may have to install the Suggested packages.

---

### Post by airwolf on 2007-11-22
[Try this.]("http://ubuntuforums.org/showpost.php?p=3813572&postcount=5")

---

### Post by disturbedite on 2007-11-22
ktorrent is the best torrent app imo.

---

### Post by jpkotta on 2007-11-24
I just updated Azureus, and it broke because of Icedtea Java.  It appears that this is a 64-bit bug.  

You can edit the launcher script like this: [http://ubuntuforums.org/showpost.php?p=3831178&postcount=10](http://ubuntuforums.org/showpost.php?p=3831178&postcount=10)

Or you can tell it which Java to use: [http://ubuntuforums.org/showpost.php?p=3831178&postcount=9](http://ubuntuforums.org/showpost.php?p=3831178&postcount=9)

[https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/157162](https://bugs.launchpad.net/ubuntu/+source/azureus/+bug/157162)

---

