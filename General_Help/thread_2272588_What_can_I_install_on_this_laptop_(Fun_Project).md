---
title: "What can I install on this laptop (Fun Project)"
date: 2015-04-07
forum: General Help
---

### Post by HowIsThisWorking on 2015-04-07
Hello,

I have a VERY old laptop that I want to resurrect. I was wondering what I could install on it.

Info:
300 Mhz Proc
128 Mb Ram
Floppy Drive Addon
PCMCIA Ethernet
60GB IDE HDD (Originally 2 GB but I had a spare)
1 USB port (Non-bootable)

This is more of a list of failed attempts than it is a question but any advice would be appreciated!

Attempt 1:
Install Windows 3.1 (Yes I legally own all 12 of the floppy disks)
Installed DOS 5
Upgraded to DOS 6
Installed Windows 3.1
No network access...
No usb support...
MINESWEEPER!!! (WIN!)

Attempt Successful but VERY limited

Attempt 2:
Install Ubuntu using Debian Sarge floppy disks.

Booted system
Had network access
Used to get a newer debootstrap for ubuntu 10.04 (non-pae) install.
debootstrap crashes

Attempt FAILED...

Attempt 3:
Install Debian Sarge using floppy disks.

Booted system
Had network access
Downloaded install data
Installation successful
Tried to update
Error * Error = Error^2
Non functional, keeps crashing

Attempt FAILED...

This is where things get interesting

Attempt 4:
Install Ubuntu minimal from Dos 6

Installed Dos 5
Upgraded to Dos 6
Used Debian boot disks to use wget to download GRUB4DOS
Booted the ISO into ram with grub (hd32 if I remember correctly)
ISO Loaded Successfully!
Attempted installation
hangs after configuring network 
Can still use "live" shell (ALT + F2) but does not seem to make any progress after 12+ hours of waiting...

Attempt FAILED...

Attempt 5:
Install Lubuntu from Dos 6

Installed Dos 5
Upgraded to Dos 6
Used Debian boot disks to use wget to download GRUB4DOS
Booted the ISO into ram with grub (hd32 if I remember correctly)
ISO Loaded Successfully!
Computer resets, not enough ram... (Should have seen that one coming...)

Attempt Failed

Attempt 6:
Install Tiny Core Linux (Core 6.1) from Dos 6

Installed Dos 5
Upgraded to Dos 6
Used Debian boot disks to use wget to download GRUB4DOS
Booted the ISO into ram with grub (hd32 if I remember correctly)
ISO Boots Successfully!
Used the tutorial to copy settings to HDD
had to format drive to save settings (If I messed this up I would have to redo A LOT of config settings...)
Restarted the computer

Attempt SUCCESS!!!!
I can boot Tiny Core 6.1 Command Line without a floppy drive!
Now I need to figure out how to load it from the HDD instead of ram.

I will post any other attempts and any details if anyone requests it until I find an installation I am happy with.

What should I try to install next?

Thanks for any advice!!!


Installation Tools

[http://www.giannone.ch/rescue/current/](http://www.giannone.ch/rescue/current/)   Boots minimal linux with network support.
[https://www.plop.at/en/bootmanager/download.html](https://www.plop.at/en/bootmanager/download.html)   Attempt to boot using USB loader with non-supporting BIOs.
[http://archive.debian.org/debian/dists/sarge/main/installer-i386/current/images/floppy/](http://archive.debian.org/debian/dists/sarge/main/installer-i386/current/images/floppy/)   Attempt at installing Ubuntu/Debian via net install. Also, alternative net support (I can list details if requested).
[http://www.allbootdisks.com/download/dos.html](http://www.allbootdisks.com/download/dos.html)   I tested the previous installs with Dos6.22.img and seem to get the same results as the dos install disk I have.
[http://sourceforge.net/projects/grub4dos/](http://sourceforge.net/projects/grub4dos/)   Grub4Dos download. I extracted it and copied it to a floppy using another computer.

---

### Post by dragonfly41 on 2015-04-07
Have you read this sticky .. right at the top of the forum ..

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)


You could start by trying Puppy .. [http://murga-linux.com/puppy/viewtopic.php?t=29356](http://murga-linux.com/puppy/viewtopic.php?t=29356)

and then work your way upwards.

---

### Post by HowIsThisWorking on 2015-04-08
Hello dragonfly41 and thanks for the response!

When I get a chance I will run **sudo lshw -C cpu | grep -i sse2** and see what the response is. The laptop is from before the year 2000 so I don't know how much this will help. Also, believe it or not, Puppy linux is too large for me to run! The nonpae install is ~200M and, because I have to load it to ram (128M Max) It resets the computer when I try to load it.

---

### Post by dragonfly41 on 2015-04-08
Dropping down a gear .. try this .. [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by ProjectKITT on 2015-04-08
I was also going to say Puppy! It's been a few years since I've used it, but there are several versions and I'd certainly try it on an old laptop like that (hmm, my old Dell... XD). Perhaps there is an older version that would work on yours?

I found a list of versions here, some appear to be under 128MB: [http://puppylinux.org/wikka/PuppyVersion](http://puppylinux.org/wikka/PuppyVersion)

Good luck with whatever you decide to try!
-ProjectKITT

---

### Post by HowIsThisWorking on 2015-04-10
My dumbness (<---- Not a real word...) has reached its maximum! I tried installing ubuntu 12.04 non-pae but recieved a kernel error. I had read about someone having a similar problem with ubuntu 10.04 mini taking ages to load. So, I tried to install Ubuntu 10.04 mini one more time. It appeared to be hanging for a while (> 12 hours...) and then I forgot to shut off the computer when I went to sleep. When I woke up, it had advanced to the next screen!!! The install is finishing now. Will let you all know how I did it if it works correctly, and the layout I choose for a minimal GUI.

---

### Post by yancek on 2015-04-10
Two other possibilities that are under 100MB installed are Slitaz and TinyCore.  I believe TinyCore is 16MB installed.

---

