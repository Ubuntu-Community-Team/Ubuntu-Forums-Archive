---
title: "sudo blkid, and fdisk -l will not display IDE drives"
date: 2013-03-17
forum: General Help
---

### Post by GMHilltop on 2013-03-17
I folks.  This is the first time I have run into this situation.  I have a nice little system - a tad older, but run very well. It is an ASROCK MOBO that can run both IDE and SATA drives. To reduce the possibility of conflict I have disabled the SATA controller in the BIOS and set the IDE controller to 'Primary' - although I have tried it with both a couple of times and it still does not work.  When booting from a live CD or USB image and going to terminal: ```
sudo blkid   and    sudo fdisk -l    
```  do not list the drive.  (IDE it is set to 'master' and is on the master plug of the IDE cable.  I can see, access, and manipulate files in the os when I mount the drive, so it is not like the system can't use it.  I just don't understand why these commands are not working.  Has anyone run into this before?

---

### Post by oldfred on 2013-03-17
Old IDE drives controlled booting with jumpers on drive. Master or slave and BIOS only could boot the drive with the jumpers set to master. 
New BIOS allowed cable select jumper and you had to use the newer 80 conductor cable, not older 40 conductor like CD may have. Drives have to be jumpered for cable select with correct cable.

       [http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by GMHilltop on 2013-03-24
Thanks for the Reply oldfred.  

It is the older 40 wire cable.  Would the 80 wire cable make that much of a difference???  

I have made sure that the drive (the only one connected to the system) is jumpered as "Master" and is plugged into the Black connector (closest to the grey slave connector). 
The other end of the ribbon is connected to the Blue connector on the Motherboard.  
Still no luck with the blkid command in terminal.  

I have been able to install ubuntu to the drive, and even AFTER the installation the blkid command does not show anything at all.  

Out of curiosity I removed the IDE drive and connected a sata drive to the system (the mobo has IDE and SATA capabilities & the sata drive was the only drive connected).  
Then I booted from the live cd image I had installed on the usb stick again.  
It would not detect that SATA drive either.  

It almost sounds like a Hardware compatibility issue (I have checked the bios and both IDE and SATA controllers are enabled), and again it doesn't make sense that EVERYTHING else - including full on installations - seem to work, but that command does not work in terminal from either a live cd or a full installations terminal.  

I just don't get it.

Suggestions anyone?  

Thanks.

---

### Post by schragge on 2013-03-24
> **GMHilltop said:**
> I can see, access, and manipulate files in the os when I mount the drive, so it is not like the system can't use it.You can mount it from inside *live* system? Does it get displayed in the output of *lsblk*? And *lsblk -a*?

---

### Post by GMHilltop on 2013-04-03
This is bizarre!  I found out it has to do with the BIOS having the Floppy Drive enabled!  here is the link: [http://forums.linuxmint.com/viewtopic.php?f=46&t=128758&p=705348#p705348](http://forums.linuxmint.com/viewtopic.php?f=46&t=128758&p=705348#p705348)

---

