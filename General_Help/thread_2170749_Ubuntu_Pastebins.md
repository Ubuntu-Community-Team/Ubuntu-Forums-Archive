---
title: "Ubuntu Pastebins"
date: 2013-08-27
forum: General Help
---

### Post by sakari2 on 2013-08-27
I need help with this [http://paste.ubuntu.com/6029716/](http://paste.ubuntu.com/6029716/) can someone tell me that what is the broblem?

---

### Post by 1/0 on 2013-08-27
Hi and welcome to the forum!

Care to give some more hints on the problem. I.e. is your computer starting? Does it freeze on booting. If so, when/what do you see? 

Just from glancing through the output, I noticed you have /dev/sr0. Any idea of why sr0?

---

### Post by oldfred on 2013-08-27
sr0 is the CD.

It looks like you are installing the 32 bit version?
And a 64GB drive, is that a SSD?

Nothing stands out as an error.
What system is this?
What video do you have?
With only one system installed you will not get a grub menu by default. You have to hold shift key from BIOS until menu appears.

---

### Post by sakari2 on 2013-08-27
When i start the computer, this message comes: attempt to read or write outside of disk 'hd0'

---

### Post by oldfred on 2013-08-27
That type of error is most often when a partition table entry is beyond the end of the drive. But yours looks correct.

---

### Post by sakari2 on 2013-08-28
Hmm. Laptop is very old, hp compaq nx8220 and i use new ssd transcend 64Gt. Is there some broblem with that. And i'm not new ubuntu user, i have used it very long time... I still do not understand that problem although i'm pro programmer

---

### Post by 1/0 on 2013-08-28
> **sakari2 said:**
> Hmm. Laptop is very old, hp compaq nx8220 and i use new ssd transcend 64Gt. Is there some broblem with that.

I doubt that is causing this. This sounds like a problem configuring grub. Just an idea: try to change the grub config to set root to /dev/sda1 instead of UUID. I remember this being a problem once. You'll probably have to do this from the usb/cd/dvd, since you probably can't access the recovery mode.

---

### Post by oldfred on 2013-08-28
Specs say that is a Pentium M? And how much RAM.
Full Ubuntu with Unity needs a lot of RAM and a good video system.
You may do better with Lubuntu.
But some Pentium M have the PAE issue. You may need the non-PAE version.
And not sure then if SSD will work well. 

 [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

---

