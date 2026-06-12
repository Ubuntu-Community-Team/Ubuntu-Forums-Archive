---
title: "F.U.B.A.R. Windows/Ubuntu dual boot catastrophe"
date: 2008-01-08
forum: General Help
---

### Post by Cravethought on 2008-01-08
I've been trying to get my system to dual boot Ubuntu/Windows XP for a little while, butI've given up on it for now. I'd be content with getting my GUI back.

I tried installing Windows XP to a partition after installing Ubuntu, but my system turned off halfway through (and continued to do so). Afterwards, my system would not boot to Linux, and gave me a "Error loading Operating System" message. I fixed that, however, by reinstating GRUB. Now when I turn on my computer, it goes to a blank screen for awhile, but eventually I end up at a command line. Nothing else, just a black screen with a command line.

I've tried both startx and gdm, but startx will not work and when trying to start gdm with sudo it says it's already running. When i try to reboot it spews a bunch of "preparing to reboot"-type  messages, says it's rebooting, but does nothing.

I'd like my Ubuntu back. Using Gutsy 7.10

Anyone have any ideas?

---

### Post by jespdj on 2008-01-08
The easiest way to get a dual-booting Windows / Ubuntu system is to install Windows first, and then Ubuntu. During the installation of GRUB, Windows will automatically be added to the GRUB boot menu.

To access your Ubuntu partition, try booting with the Ubuntu installation CD. It should automatically find and mount your Ubuntu partition, so that you can save any data on it before you re-install the OS'es.

---

### Post by Cravethought on 2008-01-08
So are you suggesting that I just say "screw it" to what I have and reinstall with Windows first this time?

It's doable, because the boot disk isn't doing what you said it would.

---

### Post by zipperback on 2008-01-08
If you need help getting your system up and running with a dual boot configuration check out this link.
[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)


If you want to just get Ubuntu installed but are having problems with the GUI livecd version installation process, you might want to download and use the Alternate installer version. It uses a text based installer rather than a gui installer.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check the box at the bottom of the page that says the following.

> 
Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer


It will give you the same fully functioning desktop system, but the installation process is a little different.


- zipperback
:popcorn:

---

### Post by Cravethought on 2008-01-08
> **zipperback said:**
> If you need help getting your system up and running with a dual boot configuration check out this link.
[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)


If you want to just get Ubuntu installed but are having problems with the GUI livecd version installation process, you might want to download and use the Alternate installer version. It uses a text based installer rather than a gui installer.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check the box at the bottom of the page that says the following.



It will give you the same fully functioning desktop system, but the installation process is a little different.


- zipperback
:popcorn:

Ubuntu IS installed though. Though it's too late now (I got impatient and deleted my partitions), something with my Windows install screwed up, due to a shutting down problem with my Windows boot cd. The problem still hasn't been fixed, so if you can help, the link can be found here:

[http://ubuntuforums.org/showthread.php?t=661543](http://ubuntuforums.org/showthread.php?t=661543)

---

