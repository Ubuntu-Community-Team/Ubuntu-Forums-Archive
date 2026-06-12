---
title: "Possible return to Windows XP"
date: 2007-04-24
forum: General Help
---

### Post by liberalist on 2007-04-24
Dear sir/madam,

I am planning to install Kubuntu 6.06.1 LTS on my Windows XP PC, because I am not able to reinstall XP. However, I might switch back to XP (if it turns out I cannot work with all my software for my business). Is it possible to install Windows XP again and remove Kubuntu completely from my system (i.e. a "clean install")? And if so, how could I do this (just booting to the CD through BIOS and then follow on-screen instructions?)? Thank you very much for your answer in advance.

PS: I do **not** want a dual-boot, since I don't have enough hard-disk space.

---

### Post by jespdj on 2007-04-24
Why do you say "...because I am not able to reinstall XP"?

If you have a Windows XP installation CD then you can ofcourse re-install Windows XP. During the Windows XP installation procedure you can delete your Ubuntu partition(s) and create a new partition to install Windows XP on.

---

### Post by GeirG on 2007-04-24
Last time I installed any Windows variant I had the option to use the whole disk (i.e. erase everything currently there). I would be amazed if this has changed

Good luck

---

### Post by JerseyShoreComputer on 2007-04-24
You can install XP and wipe out the whole hard drive (format it) and install it clean and fresh. Or you can partition the drive and share XP and Ubuntu on the same computer. Before you wipe out Ubuntu for XP, give it a good try.. Work with the Open Office programs and see you can share files with MS Office users.

But nothing has changed in the Windows install.. Same options... Think long and hard before you go back to XP..

---

### Post by liberalist on 2007-04-24
Thanks for your replies. I have a very stupid question next, I don't know how to start-up from my Kubuntu 6.06.1 LTS CD. I tried pressing the 'C' key during start-up and the delete button (I read somewhere this opens BIOS, but it didn't). I couldn't find how to install Kubuntu in the Desktop guide. So, how do I install it (especially how do I start-up my computer from a CD)?

> **jespdj said:**
> Why do you say "...because I am not able to reinstall XP"?

If you have a Windows XP installation CD then you can ofcourse re-install Windows XP. During the Windows XP installation procedure you can delete your Ubuntu partition(s) and create a new partition to install Windows XP on.

I cannot install XP again. When I tried, the button "Continue" was dimmed out because my version of XP was newer than the version to be installed (very strange error).

---

### Post by Yoooder on 2007-04-24
> **liberalist said:**
> Thanks for your replies. I have a very stupid question next, I don't know how to start-up from my Kubuntu 6.06.1 LTS CD. I tried pressing the 'C' key during start-up and the delete button (I read somewhere this opens BIOS, but it didn't). I couldn't find how to install Kubuntu in the Desktop guide. So, how do I install it (especially how do I start-up my computer from a CD)?



I cannot install XP again. When I tried, the button "Continue" was dimmed out because my version of XP was newer than the version to be installed (very strange error).

My understanding of your situation is that you can't get your machine to boot from CD (Windows or Linux) and you're Windows re-installation errors occur if you try running the CD from within Windows.  Right?

If this is the case, you were on the right track trying to get to your BIOS.  If you shut your computer down and then turn it back on it should first display your video card information followed by your machine statistics or a logo and should beep.  Watch the screen carefully, and somewhere it might say "press [x] for setup" or something similar.  Pressing that key will get you to your BIOS/CMOS config.

A few of the most common keys used for this are:
 - F1
 - F2
 - F12
 - Del
 - Esc

Once you're in your BIOS then you need to find your "Boot Order" or "Boot Device" or "Startup Order" setting (might be under a different name, but you get the gist).  Once you find it you'll need your CDROM to boot before your Hard Drive.

Save your change and reboot, and you should be able to boot to the Ubuntu or Windows CD's.  If you decide to re-install Windows, just pop in your Windows CD and reboot.  You'll have to press a key when it asks, but once you're in the installer you'll have the option to delete all partitions and install Windows on a clean slate.

---

### Post by liberalist on 2007-04-24
> **Yoooder said:**
> My understanding of your situation is that you can't get your machine to boot from CD (Windows or Linux) and you're Windows re-installation errors occur if you try running the CD from within Windows.  Right?
Yes, that is correct.

> **Yoooder said:**
> Once you're in your BIOS then you need to find your "Boot Order" or "Boot Device" or "Startup Order" setting (might be under a different name, but you get the gist).  Once you find it you'll need your CDROM to boot before your Hard Drive.. (...)
Thanks for your help, but it is correct that I need to press the delete button to get into BIOS and then X? Or should I hold the delete button or tap it? 

Is it a problem if the CD is already present in the disc drive when starting up my computer? 

Furthermore, I have a Service Pack 1 CD, so a lot of updates need to be installed (probably 300+) and that is going to make my system quite slow (not to mention all the trouble with XP). What do you recommend: install Kubuntu or XP? On Kubuntu most Microsoft Office documents can be opened with OpenOffice 2, right? Furthemore, can I use my Hewlett Packard PSC 2410 Photosmart All-in-One Printer on Linux? There isn't an installation CD for Linux, namely ([not on HP's official website either]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=303753&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&lang=en&cc=us")). I don't mind if I cannot scan documents (although it would be nice), but to print documents would be a requirement, actually. Do I need to install Wine (this enables to run some Windows programs, right?) or is this printer supported in Linux? 

**Update:** I couldn't find a driver for my printer at [http://hpoj.sourceforge.net/suplist.shtml](http://hpoj.sourceforge.net/suplist.shtml) as well. 
Found a good application that **supports my printer** :) [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

Thank you very much in advance.

---

### Post by liberalist on 2007-04-24
> **Yoooder said:**
> If this is the case, you were on the right track trying to get to your BIOS.  If you shut your computer down and then turn it back on it should first display your video card information followed by your machine statistics or a logo and should beep.  Watch the screen carefully, and somewhere it might say "press [x] for setup" or something similar.  Pressing that key will get you to your BIOS/CMOS config.

I have to press F2 to get into BIOS. However, cannot find a way to boot from the disk drive. I have found an interesting document at [http://www.cyberwalker.com/article/28](http://www.cyberwalker.com/article/28) , so I am going to read this and see if I can find out what to do. If you know how to solve this problem, you are more than welcome to help.

---

### Post by liberalist on 2007-04-24
It worked :), I have booted into Kubuntu (Live CD). 

However, I cannot connect to my wireless home network. My computer has a built-in wireless card from Dell (I think). The Wireless Assistant does detect my network SSID. I clicked on it and answered the questions of the wizard. I use automatic connection (DHCP) and entered my 64-bits WEP-key (I tried using Open/Shared key types as well as ASCII on/off, but nothing worked). 

How can I connect to the internet? Thank you very much in advance.

Update: I looked in the KInfoCenter and I found that my wireless card is called Intel Corporation Pro Wireless/LAN 2100 3B Mini PCI adapter (rev 04). At [http://ipw2100.sourceforge.net/](http://ipw2100.sourceforge.net/) I found a possible driver, but I don't really know how to install it. Thank you very much in advance.

---

### Post by liberalist on 2007-04-24
Hi everyone,

Kubuntu 6.0.1 LTS is now up and running and I must say that I am impressed. It is so easy to use (easier than Windows in some cases) and all my documents and other files can be opened with ease. Furthermore, my notebook has never been faster. It must be a very stable OS, too, since I haven't had any crashes :)

Thank you all for the excellent support and many thanks to the developers of Kubuntu, this Linux distribution is superb.

It'd appreciated if you could answer my question in the previous post. Thank you in advance.

---

