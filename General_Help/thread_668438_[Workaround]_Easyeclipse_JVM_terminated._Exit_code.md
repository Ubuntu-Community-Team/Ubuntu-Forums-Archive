---
title: "[Workaround] Easyeclipse JVM terminated. Exit code=1"
date: 2008-01-15
forum: General Help
---

### Post by mexpolk on 2008-01-15
**[COLOR="Red"]*** THIS SOLUTION DIDN'T WORK AFTER ALL, SEE WORKING SOLUTION BELOW (Manually installing JRE and JDK) ***[/COLOR]**

I have found some workaround... and should work without problems.

1. Install Java enviroment:

$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin

2. Update alternatives:

$ sudo update-java-alternatives -s /usr/lib/jvm/java-6-sun

[B]3. Install eclipse:

$ sudo apt-get install eclipse

4. Once that Eclipse IDE is installed, download Easyeclipse and extract the contents of the tar file:

tar -zxvf Desktop/easyeclipse-lamp-1.2.2.2.tar.gz

5. Finally copy al the contents of easyeclipse-lamp-1.2.2.2/plugins to /usr/local/lib/eclipse/plugins/[/B]

And that's it! You got Eclipse with all the functionality of Easyeclipse for LAMP (or whatever the flavor you need).

Best!

---

### Post by mexpolk on 2008-01-16
Update:

There's also a need to start eclipse with -clean option from command line. Thus resolves a problem with JavaScript editor plugin.

[http://www.myeclipseide.com/PNphpBB2-viewtopic-p-54108.html]("http://www.myeclipseide.com/PNphpBB2-viewtopic-p-54108.html")

grets...

---

### Post by mexpolk on 2008-01-16
The above solution didn't work after all. It seems to be a problem of sun-java6-* packages, or I'm doing something wrong.

So I installed JRE and JDK manually and everything works fine now. Here's the solution:

1. Remove all installed packages related to java:

```

$ sudo apt-get remove eclipse sun-java6-*

```

2. Download self extracting versions of JRE and JDK for Linux (jdk-6u4-linux-i586.bin and jre-6u3-linux-i586.bin). I will assume that you downloaded them in your Desktop for the rest of the instructions (~/Desktop).

3. Create the /usr/lib/jvm directory and extract the JRE and JDK binaries there:

```

$ sudo mkdir /usr/lib/jvm
$ cd !$
$ sudo sh ~/Desktop/jre-6u3-linux-i586.bin
$ sudo sh ~/Desktop/jdk-6u4-linux-i586.bin

```

4. Install java plugin for Firefox:

```

$ sudo ln -s /usr/lib/jvm/jre1.6.0_03/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so

```

5. Update alternatives for JDK (I don't really know why we must do this, any comments to clarify this will be appreciated):

```

$ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.6.0_04/bin/java" 1

```

6. Set /usr/lib/jvm/jdk1.6.0_04 as your first java option:

```

$ sudo vim /etc/jvm

```

The file must have in the first line /usr/lib/jvm/jdk1.6.0_04 to set that directory as your first JVM search option:

```

# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

**/usr/lib/jvm/java-6-sun**
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

```

6. Verify your JRE plugin installation for Firefox by visiting [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp) and click on "VERIFY INSTALLATION" button.

7. Verify your JDK installation by typing the following in the console:

```

$ java -version
[B]java version "1.6.0_04"
Java(TM) SE Runtime Environment (build 1.6.0_04-b12)
Java HotSpot(TM) Client VM (build 10.0-b19, mixed mode, sharing)[/B]

```

And that's it! You're now able to run Easyeclipse.

Happy hacking!

---

### Post by r57 on 2008-01-18
Well...

a) after all this stuff I cannot run command java -version. When I tried Ubuntu offered me packages where I should find java program. 

b) Firefox also thing there is no java installed and offers me to install plugin.

c) easy eclipse still wont start...

---

### Post by wiesbert on 2008-01-19
I got the same errors, after trying for hours i followed this:
[http://ubuntuforums.org/showthread.php?t=671020&highlight=eclipse](http://ubuntuforums.org/showthread.php?t=671020&highlight=eclipse)

and it works now.

HTH
wiesbert

---

### Post by lippe8211 on 2008-01-25
Hi!

I solved my problem through this 

[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/184169]("https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/184169")

just enter these simple commands:
```

wget http://launchpadlibrarian.net/9590664/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8_i386.deb
sudo dpkg -i xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8_i386.deb

```

and get back to rock n roll with eclipse!

:guitar:

---

### Post by dpolishannu on 2008-04-21
Probably some one finds here in any day now...

See also this:

[http://bugs.archlinux.org/task/10066](http://bugs.archlinux.org/task/10066)

and this

[http://bbs.archlinux.org/viewtopic.php?id=47353](http://bbs.archlinux.org/viewtopic.php?id=47353)

---

