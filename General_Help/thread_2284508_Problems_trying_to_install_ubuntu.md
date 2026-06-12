---
title: "Problems trying to install ubuntu"
date: 2015-06-29
forum: General Help
---

### Post by Denson_Sanders on 2015-06-29
Hello, everyone.
So today I tried to install ubuntu 11.10 on a recently wiped laptop from the CD.
The problem is that, after the PC booted the CD, i got a black, not backlit screen, with a bunch of tiny repeating screens in which i could see the mouse pointer moving.
I have no idea what i did wrong, since I already used that same CD to install it on an other computer.
Has anyone had this kind of problem before?
The laptop is a Dell Inspiron 14 2640, if that helps.
Thanks in advance.

---

### Post by oldfred on 2015-06-29
11.10 is obsolete as of April 2013.

You can install 12.04LTS or 14.04LTS as the are long term support versions. 
If an older computer you may need Lubuntu or Xubuntu but they have different support until dates.

What video chip does that system have, and how much RAM?

---

### Post by Denson_Sanders on 2015-07-01
I could try a newer version, but my problem now actually expands, since i tried to use Hiren's Boot only to find the exact same problem ocurring.
The system has 6Gb of RAM, and a nvidia 1gb video card. How do I check for the video chip?
Thanks, once again.

---

### Post by oldfred on 2015-07-01
If you have the nVidia card what model? 
There are multiple different nVidia drivers based on verson. Current version is only for current models. And installing incorrect one makes for major issues and you have to totally remove/purge all the old nVidia before installing correct version.

Black screen then means you probably need nomodeset. With my nVidia card, it turned monitor off, but I could still see flash drive working and system booting. I always had to use nomodeset.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by Denson_Sanders on 2015-07-02
The card is Geforce GT620M.
How should i go about changing the grub, as you said, since I can't see the screen? Sorry, I'm quite new at this.
Should i insert the disc in a working computer?
I looked at the links, and maybe the command for hybrid Nvidia might work, I just need to know how to change that.

---

### Post by Denson_Sanders on 2015-07-02
It seem either nomodeset or nouveau.blacklist=1 worked, big thanks for the help.

---

