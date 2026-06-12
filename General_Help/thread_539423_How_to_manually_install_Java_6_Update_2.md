---
title: "How to manually install Java 6 Update 2"
date: 2007-08-31
forum: General Help
---

### Post by Netsurfer on 2007-08-31
[SIZE="2"]After reading a lot of posts about Java and updating (auto or manual) I tried myself to update from Java1.6.0 to Java 1.6 update 2 (which fixes also a Compiz-Fusion dislplay bug).

The procedure is very simple.

First remove any reference to old java vm using
   **  sudo apt-get remove sun-java***

then donwloading **jre-6u2-linux-i586.bin** from **[www.sun.com](www.sun.com)** to your home dir
and execute the following script to install...

sudo mkdir /usr/lib/jvm
sudo mv ~/jre-6u2-linux-i586.bin /usr/lib/jvm
cd /usr/lib/jvm
sudo chmod +x jre-6u2-linux-i586.bin
sudo ./jre-6u2-linux-i586.bin

Now you have a dir /usr/lib/jvm/jre1.6.0_02 and you can also delete jre-6u2-linux-i586.bin file.

Configuring symbolic links to Java update 2.

cd /usr/bin
sudo ln -sf /usr/lib/jvm/jre1.6.0_02/bin/java java
sudo ln -sf /usr/lib/jvm/jre1.6.0_02/bin/java_vm  java_vm
sudo ln -sf /usr/lib/jvm/jre1.6.0_02/bin/javaws  javaws
sudo ln -sf /usr/lib/jvm/jre1.6.0_02/bin/jcontrol jcontrol
sudo ln -sf /usr/lib/jvm/jre1.6.0_02/bin/keytool keytool
cd /usr/lib/firefox/plugins
sudo ln -sf /usr/lib/jvm/jre1.6.0_02/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

Edited: Warning: for editing problem there is an extra space between "libjavapl" and "ugin_oji.so"
The correct names are both libjavaplugin_oji.so
Sorry.


Verify if all is OK using command:
**$ java -version**
results...
[I]$ java version "1.6.0_02"
$ Java(TM) SE Runtime Environment (build 1.6.0_02-b05)
$ Java HotSpot(TM) Client VM (build 1.6.0_02-b05, mixed mode, sharing)[/I]

Finaly, edit the file /etc/jvm putting the complete path to java at the top of the list as follow:
$ sudo gedit /etc/jvm

...
[I]# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

**[COLOR="Red"]/usr/lib/jvm/jre1.6.0_02                     <<<------- new path[/COLOR]**
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr[/I]
...

The Java Control Panel start with "jcontrol". You can create a menu item to do that task.

That's all. :)
Bye[/SIZE]

---

### Post by Shin_Gouki2501 on 2007-08-31
forum is nice but IMO u shoudl write this into a wiki thats better for search IMO

---

### Post by Netsurfer on 2007-08-31
Thank you for suggestion. I new to that. How can I access to wiki?

---

### Post by Netsurfer on 2007-08-31
I found myself how to connect to wiki.
Bye

---

### Post by et voilà on 2007-09-01
Thank you for the How-to Netsurfer!

However this line wasn't able to modifiy libjavaplugin_oji.so on my computer for the Firefox plugins
sudo ln -sf /usr/lib/jvm/jre1.6.0_02/plugin/i386/ns7/libjavapl ugin_oji.so libjavaplugin_oji.so

I had to do it in two steps
sudo ln -sf /usr/lib/jvm/jre1.6.0_02/plugin/i386/ns7/libjavapl ugin_oji.so
sudo ln -sf /usr/lib/jvm/jre1.6.0_02/plugin/i386/ns7/libjavapl libjavaplugin_oji.so

Ciao

---

### Post by Netsurfer on 2007-09-01
There was an error on link to firefox: yoe have to delete the "space" between "..pl ugin..."
 as follows:

libjavaplugin_oji.so

Sorry. It was a typewriter error..

Ciao

---

### Post by Netsurfer on 2007-09-01
There was an error on link to firefox: yoe have to delete the "space" between "..pl ugin..."
 as follows:

      libjavaplugin_oji.so
                                                                                                             

Sorry. It was a typewriter error..

Ciao

---

