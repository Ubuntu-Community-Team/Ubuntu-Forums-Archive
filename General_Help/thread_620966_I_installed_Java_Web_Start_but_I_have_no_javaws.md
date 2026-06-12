---
title: "I installed Java Web Start but I have no javaws"
date: 2007-11-23
forum: General Help
---

### Post by Starlight on 2007-11-23
Hi! I have a really weird problem. I installed "Sun Java 6 Web Start" using the Add/Remove program... but I can't actually run any Java Web Start stuff. I've read somewhere that the command "javaws" is used to do it, but it seems I don't have it. When I type "javaws" in a console, and press enter, here's what it says:

The program 'javaws' is currently not installed.  You can install it by typing:
sudo apt-get install j2re1.4

The problem is that I've already installed Java 6 Web Start, and I didn't get any errors during the installation. I can't use Java 1.4, because what I'm trying to run needs Java 1.6 :( 

I have the "java" command, but when I try to run a .jnlp file with it, I get an error...

---

### Post by tempest on 2007-11-23
Are you using 64bit Gutsy? I only use javaws at work so I had not noticed that my home computer with 64bit Gutsy does not even have javaws in with the other binaries. I was reading somewhere that the 64bit version of Java 6 does not have a Firefox plugin, Maybe there is also no javaws?

---

### Post by Starlight on 2007-11-23
Hi tempest! Yes, I'm using the 64bit version. But it's really strange that when installing "Java 6 Web Start" it installed Java, but without Web Start...

---

### Post by tytuz on 2008-05-31
Hi there!

It helped me out:
[http://dmartin.org/content/running-java-web-start-apps-ubuntu-linux-amd-64](http://dmartin.org/content/running-java-web-start-apps-ubuntu-linux-amd-64)

---

### Post by Sef on 2008-05-31
> I was reading somewhere that the 64bit version of Java 6 does not have a Firefox plugin,.... 

That is correct, but one is coming.  Click on my Java On 64-Bit Systems link below for more information. 

Use OpenJDK, it is available in Add/Remove.

> It helped me out:
[http://dmartin.org/content/running-j...u-linux-amd-64](http://dmartin.org/content/running-j...u-linux-amd-64)

Read [Kliz's Tutorial]("http://ubuntuforums.org/showthread.php?t=202537") on running 32-bit Firefox on a 64-bit System.

---

