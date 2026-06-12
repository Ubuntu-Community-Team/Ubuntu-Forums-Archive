---
title: "Oracle Java 7 no longer functioning"
date: 2012-12-13
forum: General Help
---

### Post by agxryt on 2012-12-13
Hey guys, 

I have Oracle's Java 7 installed on my 64-bit Lubuntu 12.04 system. 

Yesterday, everything was working fine. I was using Java, because nothing else seems to work with minecraft.

So, today comes along and the usual option to run the .jar file "with Java 7" is gone. Cool.

So, I try

```
java /home/user/Minecraft/MinecraftSP.jar
```which returns

```
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>

```So clearly java 7 is gone, right? 

Well, I used the oracle-java7-installer method mentioned here:

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

So I go to reinstall that package. It's already installed. huh.


Upon further reading, I find that you can remove Java 7 by removing the installer, so I do this. I also remove anything related to Java using the method described here:

[http://askubuntu.com/questions/84483/how-to-completely-uninstall-java](http://askubuntu.com/questions/84483/how-to-completely-uninstall-java)   (answer #3)



Reinstall everything. Still does not work. Can't select to run .jar files in java, can't use "java" command. Even though it's apparently installed.

What should I do? I'm worried that something somewhere has messed up Java's ability to run, and I'm going to have to reinstall Lubuntu. :(


EDIT: So, I'm watching youtube currently. Which I thought required Java. Removing the installer is supposed to have removed the browser-plugin. And I don't have iced-tea. Atleast, I thought I had removed it.

What is going on? haha

---

### Post by Lyfang on 2012-12-13
**Is done at your own risk and I take no responsibility for any loss or damage (as usual).** You could try to install the *oracle-java6-installer* or *oracle-java8-installer* from the webupd8team repository before reinstalling the OS.

---

### Post by agxryt on 2012-12-13
> **Lyfang said:**
> **Is done at your own risk and I take no responsibility for any loss or damage (as usual).** You could try to install the *oracle-java6-installer* or *oracle-java8-installer* from the webupd8team repository before reinstalling the OS.

Oh so I can't sue him. How unfortunate :P

Yeah, I'll give it a try!

---

### Post by agxryt on 2012-12-13
Oracle Java 8 seems to have installed correctly. I uninstalled minecraft, just in case I messed something up there. So I'll have to post when I get it installed... it's an... err.... alternate install ;P

---

### Post by Pjotr123 on 2012-12-13
Try this manual method (almost as easy as webupd8) for installing Oracle Java 7:
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

It "just works" all the time.... :-)

---

### Post by agxryt on 2012-12-13
> **agxryt said:**
> Oracle Java 8 seems to have installed correctly. I uninstalled minecraft, just in case I messed something up there. So I'll have to post when I get it installed... it's an... err.... alternate install ;P


Seems to have worked perfectly. Not only that, but the usual fix associated with it doesn't need to be done.

Thanks!

> **Pjotr123 said:**
> Try this manual method (almost as easy as webupd8) for installing Oracle Java 7:
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

It "just works" all the time.... :smile:


I got it working this time. Java 8 seems to run minecraft better than java 7. 

I'll probably do this when I reinstall my OS anyways. It'll help me learn :P

---

### Post by Lyfang on 2012-12-13
> **agxryt said:**
> Oh so I can't sue him. How unfortunate :P
Generally speaking many situations sometimes seem to be all messed up. The worst part would be to attempt to try to show a little kindness by helping, only latter to be accused of destroying everything. 
> **agxryt said:**
> Seems to have worked perfectly. Not only that, but the usual fix associated with it doesn't need to be done.

Thanks!




I got it working this time. Java 8 seems to run minecraft better than java 7. 

I'll probably do this when I reinstall my OS anyways. It'll help me learn :P
I would try to follow these instruction if you ever need Java 7 working, the link that you posted: [http://askubuntu.com/questions/84483/how-to-completely-uninstall-java](http://askubuntu.com/questions/84483/how-to-completely-uninstall-java)
Then open PCManFM, make sure that the /usr/lib/jvm folder is empty and go to /home/USERNAME, press Ctrl+h and make sure the Oracle Java directory is empty.

Uninstall the Java Plugin and reinstall the oracle-java7-installer
```
sudo rm /usr/lib/mozilla/plugins/libnpjp2.so
sudo apt-get purge oracle-java7-installer 
sudo apt-get install oracle-java7-installer 
```
Which downloads and installs jdk-7u10-linux-x64.tar.gz

You could also try to download Java for the RPM installer and convert the .rpm to a .deb file using Alien.

---

### Post by Lyfang on 2012-12-13
> **agxryt said:**
> I got it working this time. Java 8 seems to run minecraft better than java 7.
Great to hear about Oracle Java 8 working. But be considerate of these early access builds: "Oracle Java 8 should only be used for testing purposes and/or by developers. Since this is a preview release, you'll encounter bugs!" - [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html ]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html")(release expected in summer 2013)

---

### Post by Pjotr123 on 2012-12-13
I second that. Oracle Java 7u9 is the stable up to date version. Only that version can be trusted to work as predicted.

However, because of security issues (a constant concern with Java over the years) I advise to disable the Java browser plugin by default, and only enable it when needed, for as long as it's needed.

---

### Post by Lyfang on 2012-12-15
oracle-java7-installer contains a script to download and install. How about a script to uninstall Oracle Java? **@agxryt:** If the problem keeps repeating with Java try clearing the Java cache.

---

### Post by agxryt on 2012-12-17
> **Lyfang said:**
> oracle-java7-installer contains a script to download and install. How about a script to uninstall Oracle Java? **@agxryt:** If the problem keeps repeating with Java try clearing the Java cache.

I think I did that. I followed a series of instructions to remove anything java from my PC. It even removed a random file called "java" which had no association, and was in my documents. 

Pretty darn thorough. Things appear to be working now. I'm not exactly sure what happened, but I might tinker around a little more.

---

