---
title: "Project planning software needed"
date: 2018-05-21
forum: General Help
---

### Post by Nina_W on 2018-05-21
I've just uploaded Ubuntu 18.04 (previously had 16) and am finding the software center horrendous!
I am trying to find some project planning software and can't seem to find any. I know KDE do one but can't seem to find it. I've searched the web for suggestions but just keep finding old threads suggesting things for older versions of Ubuntu.

Any suggestions welcome.

---

### Post by HermanAB on 2018-05-21
Project Libre is the best.  I use it all the time.  It work better with MS Project than MS Project works with MS Project:
[https://www.projectlibre.com/](https://www.projectlibre.com/)

---

### Post by Nina_W on 2018-05-22
Many thanks. But when I go to download it, it isn't giving different options for different operating systems, which is a little odd. Does the OS option come up during the download?
I can only find this on the Project Libre site and not in the Software Uploader.

---

### Post by HermanAB on 2018-05-22
It is a Java program - cross platform.  You need to install Oracle Java.

It works very well - better than MS Project.

---

### Post by Nina_W on 2018-09-14
I've finally got around to this and seem to have it installed but it won't run. So far I have installed java
sudo apt update
sudo apt install default-jre
sudo apt install default-jdk

Then downloaded the .rpm from the Projectlibre website then

sudo apt-get install alien
cd Downloads
sudo alien projectlibre-1.8.0-1.rpm
sudo dpkg -i projectlibre_1.8.0-2_all.deb

seemed to be installing, completed without errors, if I look through my file system there are various files, similar to what I've seen with other applications. When I go to the application launcher, there is a Projectlibre icon when I click on it the launcher goes as if it is launching, but nothing happens. Also if I go the the shopping bag and look for installed software it isn't there.

Any suggestions?

---

### Post by ajgreeny on 2018-09-14
There is a problem with openjdk-11-jre at the present time and many GUI applications will not run, see the bug at [https://bugs.launchpad.net/ubuntu/+source/openjdk-lts/+bug/1788250](https://bugs.launchpad.net/ubuntu/+source/openjdk-lts/+bug/1788250)

Try the workaround at post #4 of that bug; it has worked for me and others have said the Oracle java version works fine as well so you can try either of those solutions and hopefully one or other will work for you.

---

### Post by Holger_Gehrke on 2018-09-14
With a bit of searching on the sourceforge download page you could have saved yourself the package conversion, because there's a .deb available.
Start Project Libre from the shell with 'projectlibre'. If you do it that way you'll see all the diagnostic and error messages that get hidden if you start it graphically. 
If you get ```
'Exception in thread "main" java.awt.AWTError: Assistive Technology not found: org.GNOME.Accessibility.AtkWrapper'
``` then it's the same problem (and the same solution) as in [that thread]("https://ubuntuforums.org/showthread.php?t=2400867"). Seems to only come up with projectlibre under Java 10, when I started it in Java 8 it runs whether I disable the ATK bridge or not.

Holger

---

### Post by Nina_W on 2018-09-14
> **ajgreeny said:**
> There is a problem with openjdk-11-jre at the present time and many GUI applications will not run, see the bug at [https://bugs.launchpad.net/ubuntu/+source/openjdk-lts/+bug/1788250](https://bugs.launchpad.net/ubuntu/+source/openjdk-lts/+bug/1788250)

Try the workaround at post #4 of that bug; it has worked for me and others have said the Oracle java version works fine as well so you can try either of those solutions and hopefully one or other will work for you.

#4 is now out of date, as that line is already commented out. It seems there have been a lot of recent fixes to this bug.
I tried #6 and that has worked.

Many thanks everyone

---

### Post by ajgreeny on 2018-09-14
Yes, the bug was squashed for most of us yesterday with an upgrade of openjdk-11-jre from 10.0.2+13-1ubuntu0.18.04.**1** to 10.0.2+13-1ubuntu0.18.04.**2** specifically to overcome this problem.

Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by cntrl on 2018-12-05
good day, please clarify me what should I do in /etc/java-11-openjdk/accessibility.properties
in the last line I have exactly this:
#assistive_technologies=org.GNOME.Accessibility.AtkWrapper

so please show me how must be written, thanks

---

### Post by cntrl on 2018-12-05
good day ajgreeny, I'm just installed kubuntu 18.04.2, so I have 

openjdk version "10.0.2" 2018-07-17
OpenJDK Runtime Environment (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.4)
OpenJDK Server VM (build 10.0.2+13-Ubuntu-1ubuntu0.18.04.4, mixed mode)

please let me know how should be right to solve correct launch of projectlibre, thanks

---

