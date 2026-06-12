---
title: "System Stalls During Live Session of Ubuntu 13.04"
date: 2013-04-30
forum: General Help
---

### Post by ChochiWpg on 2013-04-30
[COLOR=#000000][FONT=arial]Hi Everyone,

I was going to install Ubuntu 13.04 today via USB. I was able to boot from the USB without an issue, clicked on Try Ubuntu, just to test it out and it took about 5mins to load the desktop. I then searched for gparted in the dash to free up some space on my HD first and while searching, Ubuntu Live just showed fuzz on the screen and completely stalled. Had to do a hard shut down and restart of my computer. [/FONT][/COLOR]

[COLOR=#000000][FONT=arial]I am concerned that if during a live session the computer completely stalls/locks that it may do so during partitioning my drive.  Should I not be concerned and next time select install Ubuntu option instead of going to Try Ubuntu?  Or am I better off installing Ubuntu 12.04.2 LTS instead.  

I hear that 13.04 is much faster than 12.04.2, with new features.  But at the same time I need something stable to use on an everyday basis.  So far, even before install, 13.04 is making me a bit concerned.  Thoughts/suggestions?[/FONT][/COLOR]

---

### Post by ibjsb4 on 2013-04-30
Whats your computer specs?  Especially your video.  Do you have windows installed?

---

### Post by ChochiWpg on 2013-04-30
> **ibjsb4 said:**
> Whats your computer specs?  Especially your video.  Do you have windows installed?

AMD Phenom 8550 Triple Core Processor 2.2 GHz
4GB RAM
64 Bit OS (Currently running Vista)
NVIDIA GeForce 6150 SE Graphics

I have 200GB of free HD space, which I was going to provide Ubuntu with 100GB worth.  This is how I was going to partition my drives.

500MB /boot partition  (This is where I will install GRUB and have Windows Bootloader handle the dual boot)
20GB / partition
73.5GB /Home partition
6GB /swap partition

But 13.04 seems to stall in the Live environment.  It will be working alright for the first couple minutes than I will do a search in the dash and it will stall out on me.  It's happen everytime I have run the Live Session via USB.  I have even redownloaded and placed the ISO on the USB again.  Same issue.

I am using Universal USB Installer from pendrivelinux.com to create the USB as well.

---

### Post by ibjsb4 on 2013-04-30
I took a look in the forum for you video.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=NVIDIA+GeForce+6150SE&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=NVIDIA+GeForce+6150SE&sa=Search&cof=FORID:9)

Found this about nomodeset.

[http://ubuntuforums.org/showthread.php?t=2074758&p=12312099&viewfull=1#post12312099](http://ubuntuforums.org/showthread.php?t=2074758&p=12312099&viewfull=1#post12312099)

more on it

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

It may not be the answer, but worth a try on the live usb.

---

### Post by ChochiWpg on 2013-04-30
> **ibjsb4 said:**
> I took a look in the forum for you video.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=NVIDIA+GeForce+6150SE&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=NVIDIA+GeForce+6150SE&sa=Search&cof=FORID:9)

Found this about nomodeset.

[http://ubuntuforums.org/showthread.php?t=2074758&p=12312099&viewfull=1#post12312099](http://ubuntuforums.org/showthread.php?t=2074758&p=12312099&viewfull=1#post12312099)

more on it

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

It may not be the answer, but worth a try on the live usb.

Ok, I will have a look thanks.  I am new to Linux so this may be over my head, but I will see what I can decipher.

---

### Post by ibjsb4 on 2013-04-30
This is pretty much over my head too, since we have different hardware.  But just post back with any questions and we will see what two heads can do :)

---

