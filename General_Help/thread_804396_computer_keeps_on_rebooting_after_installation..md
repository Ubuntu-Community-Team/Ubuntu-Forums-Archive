---
title: "computer keeps on rebooting after installation."
date: 2008-05-23
forum: General Help
---

### Post by realbuntu on 2008-05-23
I completed installation of ubuntu desktop, it didn't show me any errors during the installation. After the installation, the computer rebooted, after loading bios, the screen says 'no signal', a few seconds later it reboots itself again and this repeats all by itself.

What can I do to get the system to start properly. I m completely lost.

Feedback is appreciated.
Thank you!

---

### Post by itix on 2008-05-24
Can you reach the BIOS settings? (should be one of the F1, F2, ..., F(n) keys)
If so, change to boot from CD, dowload and burn the [Super Grub Disc]("http://www.supergrubdisk.org/") and boot the computer with the disc in the tray. That should restore your system.

---

### Post by realbuntu on 2008-05-24
thanks will try it and get back to you!

---

### Post by realbuntu on 2008-05-24
It can boot up using the Super GRUB. I choose auto fix. Even it said success, then I remove the CD, rebooted. Same problem occured. So I try the advance option, got to the part where it says "Partition to Boot"

The screen came to the following:

Booting '1 hda1 sda1 (hd0,0) hd0s1 ext2fs Ubuntu 8.04 \n \l'

set out_device=(hd0,0)
set out_hurd_hd-hd0
.
.
.

Error 30: Invalid arguement 

Any advice is appreciated!

---

### Post by realbuntu on 2008-05-24
Here is some thing I found, again I have no idea where to go from here. 

Booting command-list

findf /grub/stage1 /boot/grub/stage1
root (hd1,0)
Filesystem type is ext2fs, partition type 0x83
setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
Running "ebmed /boot/grub/e2fs_stage1_5 (hd0)"... failed (this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
Running "install /boot/grub/stage1 d (hd0) /boot/grub/stage2 p /boot/grub/menu.lst " ... failed

Error 17: Cannnot mount selected partition

---

### Post by itix on 2008-05-24
Hmmm sounds wierd. I'll just check the options for my super grub disc. I have never been forced to use the advanced options part.

I'll get right back to ya.

---

### Post by itix on 2008-05-24
Woa... this isn't a GRUB error. Something's up with the Linux kernel itself.
Have you tried reistalling the system? Are you sure that you are using the right version (i386 vs amd64 etc)?

---

### Post by itix on 2008-05-24
One more thing before you go to reinstalling the system. Since you can reach grub, press escape where it says timout 3... 2.... 1... 0 etc (before it reches 0, that is).

At the menu that pops up, choose "Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)". That should reset any faults on the ubuntu and linux componenets itself.

---

### Post by realbuntu on 2008-05-24
I m using a pentium P4. 

I m currently on the amd64 version. It boots up fine if using the super grub.

First I installed the other i386, it gave me the original issue that I had posted. Then I try intaling the amd64 version. Same issue happen. Then I came here. 

I m thinking about is installing i386 and then use the super grub to try fixing to see if it works.  I think this is what I m going to do now.

Please keep in mind that I m trying to lose the super grub for booting :)

---

### Post by realbuntu on 2008-05-24
No I was not able to reach the grub. I had use the super grub to start in Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode). Then I rebooted. It had never reached the GRUB without the super.

---

### Post by realbuntu on 2008-05-24
reinstall in progress..  hope it works out. will get back to you

---

### Post by realbuntu on 2008-05-24
Thanks again for introducting me to the super grub, it really push my morale to a much higher level after seeing that the system can be booted on my computer.

---

### Post by realbuntu on 2008-05-24
only one things that gives me error is using 'boot partition' in Boot & Tools on the super grub.

Booting '1 hda1 sda1 (hd0,0) hd0s1 ext2fs Ubuntu 8.04 \n \l'

set out_device=(hd0,0)
set out_hurd_hd=hd0
set out_hd=hd0
set out_linux_letter=a
set out_lide_hd=hda
set out_lscsi_hd=sda
set out_part=(hd0,0)
set out_lide_part=hda1
set out_lscsi_part=sda1
set out_hurd_part=hd0s1
set out_linux_part=a1
set out_part_n=o
set out_linux_end=a1
back
back
set aux_part=(hd0,0)
rootnoverify (hd0,0)
chainloader +1

Error 13: Invalid or unsupported executable format


Still Unable to boot without using super GRUB. 

Suggest or advice is appreciated!

---

### Post by itix on 2008-05-24
I do hope it goes OK. I wish you the best of luck.
It was a really strange problem. The problem is usually that you can't use the Live CD but you CAN boot the system and for that, there's the alternate CD. Yours was the exact opposite.

Great to hear that you can at least boot the system. It would be kind of irritating to use the Super Grub every time you want to boot though.

---

### Post by itix on 2008-05-24
Well if that is the case, I guess your system is 64bit after all. That's wierd because the only 64 bit processors intel has done are the dual and qaud core ones, not the Pentium ones :S

This last one was with the i386 right?

---

### Post by realbuntu on 2008-05-24
Yes the last one was with i386.  I wonder if there is some hardware setting thats preventing it the boot.

---

### Post by itix on 2008-05-25
I have no idea actually. Have you built the computer yourself or is it a factory built one (i.e. Dell Insporon this-and-that, Acer Aspire this-and-that, Toshiba whateverish....)

---

### Post by realbuntu on 2008-05-27
The brand of the computer is TCL. some not well known company. I first reinstalled windows, then I use windows install, then it worked. But I was never able to get ubuntu to run alone without having windows.  

I don't know why but I have other issues now :) 

thanks again.

---

