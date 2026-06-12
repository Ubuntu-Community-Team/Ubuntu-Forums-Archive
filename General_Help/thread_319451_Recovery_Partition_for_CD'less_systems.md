---
title: "Recovery Partition for CD'less systems"
date: 2006-12-15
forum: General Help
---

### Post by lfjewett on 2006-12-15
I have a system that does not have a CD or Floppy drive ( older tablet pc ) that's running Ubuntu.  I want to create a backup of the system so if things go south in the future I can restore to the current state.  I have  a 16 GB hard disk and Ubuntu is currently on a 6 GB partition.  The remaining space is free.   What I'd like to do is create a small ( 100-600mb ) partition that is bootable.  The idea being if the computer is messed up beyond booting I can select the backup partition from GRUB menu and boot to a rescue system.  From here I can restore an Image of the system held on my homes SAN.    I was looking at MondoRescue and included Mindi applications but they seem to only inlude info on creating bootable CD or Floppy media?  Any suggestions on how to make this work best?

Thanks.

---

### Post by bodhi.zazen on 2006-12-15
> **lfjewett said:**
> I have a system that does not have a CD or Floppy drive ( older tablet pc ) that's running Ubuntu.  I want to create a backup of the system so if things go south in the future I can restore to the current state.  I have  a 16 GB hard disk and Ubuntu is currently on a 6 GB partition.  The remaining space is free.   What I'd like to do is create a small ( 100-600mb ) partition that is bootable.  The idea being if the computer is messed up beyond booting I can select the backup partition from GRUB menu and boot to a rescue system.  From here I can restore an Image of the system held on my homes SAN.    I was looking at MondoRescue and included Mindi applications but they seem to only inlude info on creating bootable CD or Floppy media?  Any suggestions on how to make this work best?

Thanks.

If you do not need the space just mirror your current install...

You can remove stuff (like Ubuntu desktop) if you do not need a GUI and want to minimize the space ....

---

### Post by lfjewett on 2006-12-16
I still need that data space.. I'm hoping I can install a small linux image to a 800MB partition that would allow me to boot, format, untar a backup of the computer if the primary partition gets hosed up.  I tried to follow the instructions here : [http://www.ubuntuforums.org/showthread.php?t=316093](http://www.ubuntuforums.org/showthread.php?t=316093)  to install ubuntu using the ISO image but each time it says it can't read the CDROM or the image is corrupt.  ( downloaded twice + tried xubuntu ).     

What I really need is a way to install ( without floppy or CD ) a small bootable linux system into /dev/hda1 for recovery purposes.   I don't need much,  a shell prompt, ssh, tar, gzip, network support, heck smbfs if possible..  Does anyone have any suggestions?

Thanks

---

### Post by bodhi.zazen on 2006-12-17
fluxbuntu takes 1.3 Gb.

[Main page](http://fluxbuntu.org/)

[forums](http://community.fluxbuntu.org/)

[Download fluxbuntu-nbuild1-rev2-desktop-i386.iso](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.iso)

MD5SUM  : 
> c054428c46a1b5ffaab4295bc7db3c9b  fluxbuntu-nbuild1-rev2-desktop-i386.iso


---

