---
title: "What does Grub stage 1.5 do?"
date: 2008-03-24
forum: General Help
---

### Post by MPH on 2008-03-24
I suspected that the HighPoint HPT366 ATA-66 disk controller chip on my Soyo SY-6BA+IV mobo was corrupting GRUB whenever I used the HPT366’s BIOS to change boot drives.  According to a post I just found at [http://forums.gentoo.org/viewtopic-p-3217132.html](http://forums.gentoo.org/viewtopic-p-3217132.html)...

> The problem with Highpoint + GRUB is that the Highpoint BIOS stores its metadata in sector 9 of each harddrive. Normally this area is unused, so GRUB puts its stage1.5 file in that area too. 

Since GRUB's stage1.5 is optional, the workaround is simple : don't use it :)
**Code:**
[COLOR="Green"]# cd /boot/grub
# rm *stage1_5
# grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit[/COLOR] 

This post refers to a newer Highpoint chip ([http://www.highpoint-tech.com/PDF/RR1522a/RR152x_User_Manual.pdf](http://www.highpoint-tech.com/PDF/RR1522a/RR152x_User_Manual.pdf)) but it showed that Highpoint has made a practice of writing BIOS metadata on the first track of the disk drives it controls.

Assuming that my HPT366 was also writing nearby the MBR, I decided to try the above recommendation.  But rather than risk deleting the stage 1.5 files, I created a subfolder and moved the stage 1.5 files to the subfolder.  Then I ran GRUB’s Root and Setup commands to reflect that change.

It worked!  Now I can change the boot drive without corrupting GRUB… but now Grub is minus stage 1.5 on my Ubuntu hard drive.  That raises two questions about GRUB:

[LIST=1]
[*]What functionality am I missing by not having stage 1.5 available?
[*]Is stage 1.5 ever recreated without reinstalling Ubuntu?  In other words, do activities like Ubuntu version upgrades or system updates ever recreate the GRUB stages?
[/LIST]

---

### Post by louieb on 2008-03-25
From what I've read  stage1.5 is used when GRUB has to read file systems other than ext2 or ext3.

---

### Post by MPH on 2008-03-25
> From what I've read stage1.5 is used when GRUB has to read file systems other than ext2 or ext3.

So does that mean that without stage 1.5, I could dual boot different versions of Linux but not dual boot with Windows?

---

### Post by MPH on 2008-03-25
Most likely, only those who have GRUB corrupted frequently will find this interesting.

I have discovered that at least two Highpoint ATA controllers, the Y2K era HPT366 chip (my personal nemesis) and the RocketRAID 152x SATA Host Adapter, write on the first track of a hard drive just like GRUB stage 1.5 does.  The latter controller’s manual ([http://www.highpoint-tech.com/PDF/RR1522a/RR152x_User_Manual.pdf](http://www.highpoint-tech.com/PDF/RR1522a/RR152x_User_Manual.pdf)) states, “*For SuSE 10.x, please format the /boot partition using ext3 format (default is reiserfs).  Otherwise, the GRUB boot loader will overwrite the **[COLOR="Red"]RAID information stored on sector 9[/COLOR]** and cause your RAID array to be broken*”.

Well, Ubuntu utilizes Grub stage 1.5 and according to Wikipedia’s account of GNU GRUB, “GRUB Stage 1.5 is located in the first 30 kilobytes of hard disk immediately following the MBR”.  Since sectors are 512 bytes each, sector 9 easily falls within GRUB Stage 1.5.  Any disk controller writing in that general area will corrupt the version of GRUB used by Ubuntu unless the PC’s owner takes action.

I suspected my HPT366 ATA controller similarly overwrites stage 1.5 since whenever I use the HPT366’s BIOS to change my PC’s boot drive, GRUB would always become corrupted.  Luckily, I happened to Google a post ([http://forums.gentoo.org/viewtopic-p-3217132.html](http://forums.gentoo.org/viewtopic-p-3217132.html)) that correlated a Highpoint RAID controller with Grub corruption problems… and it went on to say that stage 1.5 is optional, which thankfully is true in my case.

To stop GRUB from being corrupted, I moved the stage1_5 files in /boot/grub to a different folder and reinstalled GRUB in the MBR.  (The procedure is better detailed in the first post on this thread.)  Without stage 1.5 available to reinstall, the GRUB installer will change (if possible) the “next stage to load” pointer (a disk sector address) so that it points directly to GRUB Stage 2.  That pointer is stored in GRUB Stage 1, which is resident in the MBR.  GRUB Stage 2 is stored in the Ubuntu partition.  I don’t know if the stage 2 image loaded by stage 1 is the actual file in /boot/grub or if the GRUB installer copies the stage2 file to a fixed location (like the beginning of the partition) when stage 1.5 isn’t available.  If the installer doesn’t copy stage2 to a fixed location and something moves the stage2 file to a different sector address, GRUB will effectively be corrupted.

I also found a limitation when stage 1.5 is NOT optional.  [http://mirror.centos.org/centos/4/docs/html/rhel-rg-en-4/s1-grub-whatis.html](http://mirror.centos.org/centos/4/docs/html/rhel-rg-en-4/s1-grub-whatis.html) mentions that stage 1.5 is needed when the boot partition is above the 1024 cylinder threshold (around 8GB)… “*Some hardware requires an intermediate step to get to the Stage 2 boot loader. This is sometimes true when the /boot/ partition is above the 1024 cylinder head of the hard drive…*”  Thus, if your disk controller corrupts stage 1.5, make your boot partition either the first partition or at least be sure it starts within the first 8GB so that you can eliminate the need for stage 1.5 of GRUB.


I would appreciate any corrections or additions that you may have.

---

### Post by fjgaude on 2008-03-26
Thanks... it hard to come by information like this. Your efforts are much appreciated.

frank

---

### Post by MPH on 2008-03-26
Thank you, Frank.  You might be interested to know that while googling "stage 1.5", I found my first post on this thread... _it was 40 minutes old_!

Google must crawl through the Ubuntu Forums quite frequently. :)

---

### Post by Oldsoldier2003 on 2008-03-26
> **MPH said:**
> Thank you, Frank.  You might be interested to know that while googling "stage 1.5", I found my first post on this thread... _it was 40 minutes old_!

Google must crawl through the Ubuntu Forums quite frequently. :)

Google loves the Ubuntu forums because they are full of quailty content...

---

