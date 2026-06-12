---
title: "No Internet"
date: 2008-02-17
forum: General Help
---

### Post by Sveet on 2008-02-17
My parents bought a laptop recently, and they F'ed up windows vista (installled a XP driver and they had no restore points or backup CD) so i installed ubuntu. problem is it cant connect to the wireless network. i took all the security off and checked connected on this computer it worked fine, when i try on their laptop it wont connect. using 7.10 on Acer Extensa 5420/5120

---

### Post by Derspankster on 2008-02-17
I'm guessing you have a Broadcom wireless card since you say you have an Acer. Have you enabled the restricted driver for the card? Check System>Administration>Restricted Drivers Manager. You'll need to enter your password. If you find an unchecked box for your wireless card, check it and the proper restricted driver will be downloaded. 

If that doesn't help, we'll need to explore other alternatives.

---

### Post by Crafty Kisses on 2008-02-17
> **Derspankster said:**
> I'm guessing you have a Broadcom wireless card since you say you have an Acer. Have you enabled the restricted driver for the card? Check System>Administration>Restricted Drivers Manager. You'll need to enter your password. If you find an unchecked box for your wireless card, check it and the proper restricted driver will be downloaded. 

If that doesn't help, we'll need to explore other alternatives.

Possibly a NDISwrapper.

---

### Post by Sokertes on 2008-02-17
I have Broadcom Corporation BCM94311MCG wlan mini-PCI on my laptop and ndiswrapper works like a charm.

Let me know if you want to go that route and I can help you out on it.

---

### Post by Sveet on 2008-02-18
there is no restricted driver for the wireless card.

---

### Post by Derspankster on 2008-02-18
> **Sveet said:**
> there is no restricted driver for the wireless card.

What version of Ubuntu do you have running. I'm almost certain that the latest, Gutsy 7.10 has the restricted drivers screen. If you have an earlier version, you'll need to install and enable ndiswrapper yourself.  How to's are posted on this forum.

---

### Post by Sveet on 2008-02-18
no the menu is there, there is just not a restricted driver for my wireless card. i have one for ATI accelerated graphics and a firmware for broadcom 43xx chipset family. im assuming the broadcom is the one i wanted but it wont let me use it... says software source for it is not enabled.

---

### Post by Derspankster on 2008-02-18
> **Sveet said:**
> no the menu is there, there is just not a restricted driver for my wireless card. i have one for ATI accelerated graphics and a firmware for broadcom 43xx chipset family. im assuming the broadcom is the one i wanted but it wont let me use it... says software source for it is not enabled.

Take a look at this thread;

[http://ubuntuforums.org/showthread.php?t=693965&highlight=restricted+driver+repositories](http://ubuntuforums.org/showthread.php?t=693965&highlight=restricted+driver+repositories)

Hopefully, this will help.

---

### Post by Sveet on 2008-02-18
that didnt work, it was all common sense once you pointed me to the restricted drivers. i looked in the source package control or whatever its called. everything was disabled because i had no internet when i was setting up the OS. i enabled what i needed and tried restricted driver again and it worked.

---

### Post by ferdostar on 2008-02-18
> **Sveet said:**
> that didnt work, it was all common sense once you pointed me to the restricted drivers. i looked in the source package control or whatever its called. everything was disabled because i had no internet when i was setting up the OS. i enabled what i needed and tried restricted driver again and it worked.
So, do you have an internet connection now or you're still trying?

---

### Post by gnicko on 2008-02-18
Can't tell if you got it working or not. I've got the same computer and this is how I got it to work: [http://ge.ubuntuforums.com/showthread.php?t=512828]("http://ge.ubuntuforums.com/showthread.php?t=512828")

---

### Post by Derspankster on 2008-02-19
> **Sveet said:**
> that didnt work, it was all common sense once you pointed me to the restricted drivers. i looked in the source package control or whatever its called. everything was disabled because i had no internet when i was setting up the OS. i enabled what i needed and tried restricted driver again and it worked.

So, now you are working? If so, please mark this thread solved.

---

