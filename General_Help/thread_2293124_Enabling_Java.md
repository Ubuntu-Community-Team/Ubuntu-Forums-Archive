---
title: "Enabling Java"
date: 2015-09-02
forum: General Help
---

### Post by eric75 on 2015-09-02
I am trying to take a test on [www.proveit.com](www.proveit.com). It need java. 

There are 4 versions on [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp). I had trouble installing them, so I installed java from the Ubuntu Software Center. 

I entered "java -version" in terminal, to see if it's installed, and see: 

[INDENT]java version "1.7.0_79"[/INDENT]
[INDENT]OpenJDK Runtime Environment (IcedTea 2.5.6) (7u79-2.5.6-0ubuntu1.14.04.1)[/INDENT]
[INDENT]OpenJDK 64-Bit Server VM (build 24.79-b02, mixed mode)[/INDENT]

I also *enabled* java, as far as I can tell, via [https://www.java.com/en/download/help/enable_browser_ubuntu.xml](https://www.java.com/en/download/help/enable_browser_ubuntu.xml).

I followed both instructions, and tested in Firefox and Chromium (which are the 2 browsers that I have).

However, back at proveit.com, I entered a session id, then my name, then got a page that states:


[INDENT]*Oracle recommends that users download the latest version of their Java Virtual Machine, by clicking here. Please follow the prompts to install Java for free on your machine. If you are not comfortable completing the installation on your own, you may wish to contact a member of your company’s Computer Support division for help.*[/INDENT]
[INDENT][/INDENT]
[INDENT]*While our system has been tested to support Java version 1.4.2 or higher, your browser may prompt security warnings if your version is below a certain update. If you don’t want to update your version and still wish to take assessments, you will need to choose to allow Java to run, despite the security warnings.*[/INDENT]
[INDENT][/INDENT]
[INDENT]*You can access Oracle's Java Virtual Machine by clicking here. Please follow the prompts to install Java for free on your machine. If you are not comfortable completing the installation on your own, you may wish to ask a member of your company's Computer Support division for help.*[/INDENT]
[INDENT]*After the installation is complete, please reboot your computer and log back into your testing site by following the instructions provided to you.*[/INDENT]
[INDENT]*If you have already installed Java 1.4.2 or higher and are still receiving this message, it may need to be enabled.*[/INDENT]



What am I doing wrong? What do I need to do to get this thing to work?

---

### Post by QIII on 2015-09-02
Hello!

Java 1.7 is not the most recent version.  Java 1.8 is.  So you will need to install OpenJDK 8 or Oracle Java 8.

I won't go into the whole story of how they are related to each other.  Suffice it to say that many web developers are ignorant of the relationship and check specifically for Oracle Java.  For that reason, I just recommend Oracle Java.

The very easiest way to install Oracle Java 8 is by using the [installer from webupd8.org]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.htm"). 

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

This automates the download, installation and set-up of Oracle Java 8.  It also installs the Java browser plugin.

As a bonus, when Oracle updates Java 8, the PPA is updated so that your normal Ubuntu updates will keep up.

---

### Post by Double.J on 2015-09-02
Hi there!

Is [this guide]("https://help.ubuntu.com/community/Java") of any use for later versions?

JJ

---

### Post by QIII on 2015-09-02
Yes.  If you follow the parts I wrote.  :)

---

### Post by Double.J on 2015-09-02
Haha, 
Sorry[COLOR=#000000] [/COLOR]QIII your post hadn't shown yet ;)

---

### Post by QIII on 2015-09-02
Haha!  So it goes!

---

### Post by brian-mccumber on 2015-09-02
To automatically setup Java 8 environment variables - 
sudo apt-get install oracle-java8-set-default

---

### Post by eric75 on 2015-09-03
OK, so I ran the code from QIII, thank you for that.

[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.htm](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.htm) brought me to a 404 error though.

There wasn't a change in Chromium, but, it worked a little in Firefox, as I saw a new page, with this message:

Your Operating System may not be compatible with some of the assessments you have been assigned.

If there are any assessments you are unable to take from this computer their names will appear
below as plain text instead of hypertext.   After reviewing our System Requirements,
you can log in again from a compatible system and finish taking any assessments you cannot
take now.   If you have any questions, please contact your test administrator.

Alas, back to the PC.

---

