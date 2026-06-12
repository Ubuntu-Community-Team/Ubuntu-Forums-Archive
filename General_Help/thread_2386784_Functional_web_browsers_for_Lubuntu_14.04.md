---
title: "Functional web browsers for Lubuntu 14.04?"
date: 2018-03-10
forum: General Help
---

### Post by lordwillin on 2018-03-10
I installed Lubuntu 12.04 LTS on my 2007 laptop that shipped with Windows XP SP2 installed.  The Lubuntu browsers included in 12.04 (firefox and chromium) don't work on current versions of gmail and other websites.  I had installed the Opera browser though, which was working fine.

Until I upgraded to 14.04 LTS last night.  This broke Opera, and the native Chromium (version 37 I believe).  I tried to uninstall and reinstall Opera, to no effect.  It will not launch.  By now I've downloaded i386 deb packages for a number of browsers (Opera, Google Chrome, Vivaldi, newer Chromium, ..) and none of them will launch.  They all just bring up an error crash message that says "Google Chrome web browser unexpectledly closed."  The only browser that works at all is the stock Firefox (version 28) that came with Lubuntu.  But I cannot use Gmail with it.

What browsers do Lubuntu users with old hardware use to access modern websites like gmail?

Thanks in advance for any help.

---

### Post by monkeybrain20122 on 2018-03-10
Is this 32 bit OS?

---

### Post by lordwillin on 2018-03-10
Sorry, yes it is.

---

### Post by Frogs Hair on 2018-03-10
Please add some information about your hardware including cpu, memory.

---

### Post by lordwillin on 2018-03-10
Intel Core Solo T1350  1.86Ghz  32-bit  i686
1.5 gb RAM     
This is an HP Pavilion dv2100 laptop

---

### Post by mörgæs on 2018-03-10
Give it a fresh install of Lubuntu 16.04 or 17.10.1, erasing everything in the process. 

After that you should change all passwords which have been entered when you used the old operative systems and/or old browsers.

---

### Post by lordwillin on 2018-03-10
> **mörgæs said:**
> Give it a fresh install of Lubuntu 16.04 or 17.10.1, erasing everything in the process. 

After that you should change all passwords which have been entered when you used the old operative systems and/or old browsers.

A fresh install.  Oh geez, is it that bad?  Okay, I can do it.  So you're saying that something is messed up on my end, I guess.

Still, my larger questions remains.  If Lubuntu is all about keeping old hardware alive, then how do users pick a browser that is up-to-date enough to use the modern web, but won't be a resource hog on an old machine?

---

### Post by Impavidus on 2018-03-10
A fresh install isn't bad at all. The thing is, 12.04 has been unsupported for quite a while, so your system has been vulnerable. That's why mörgæs suggests to change passwords. Ubuntu 14.04 is still supported (Lubuntu 14.04 is not, but Firefox and Chromium are common to all flavours so that part should still be somewhat OK) and you should be able to install the latest version of Firefox with the normal updates. But that is assuming your hardware supports it, as Firefox 58 has some more hardware demands than a version of 4 years ago. Some details about that CPU may help:```
cat /proc/cpuinfo
```
Modern browsers need modern hardware. The primary reason why people buy new hardware is to run modern browsers, so that they can see all the useless bells and whistles of modern websites. They have to do something to boost the sales of new computers, you know. But maybe your computer is still good enough.

---

### Post by mörgæs on 2018-03-10
A Core processor supports all modern browsers. A standard Lubuntu install comes with Firefox or Chromium (I don't remember which - you can install the other if you want), and after the normal package updates you are good to go. 

I do fresh installs on a regular basis when I help people with Buntu problems. Takes around 20 minutes dependent upon the internet connection.

---

### Post by jerareyoshi on 2018-03-10
QupZilla , Min , Midori.

---

### Post by mörgæs on 2018-03-10
Midori should only be used if one has verified that the source code is maintained. Latest news I heard was that the project is abandoned:

[https://ubuntuforums.org/showthread.php?t=2371648](https://ubuntuforums.org/showthread.php?t=2371648)

Anyway: Time for a fresh install.

---

