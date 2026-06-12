---
title: "Help unhiding partitions. (Dual Boot)"
date: 2007-05-21
forum: General Help
---

### Post by SrEstroncio on 2007-05-21
This is my first time here <_<, hello everyone
I have been using Ubuntu for the past two months and I love it.
I have a compaq laptop with a partitioned 55.7GB hard drive one partition running Ubuntu and the other one windows, the problem is, ever since I installed ubuntu I 've had the AUTOCHK.exe problem in my windows partition and I haven't been able to access it
I tried unhiding my windows partition directly from the terminal (GRUB> unhide (hd0,x)) but it always tells me that the selected disk does not exist, I tried unhiding from 0 to 9 (unhide (hd0,0), unhide (hd0,1) etc) and I got the same message
Can anyone please help me? any help would be greatly appreciated
 
Here's the terminal code I got when fdisked my comp:

srestroncio@Raidne:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686   82  Linux swap / Solaris
/dev/hda2            5100        7202    16892347+  83  Linux
/dev/hda3            7203        7296      755055    5  Extended
/dev/hda5            7203        7296      755023+  82  Linux swap / Solaris
srestroncio@Raidne:~$

I'm pretty sure my windows partition is hda1 there, and I'm currently using hda2 right now.

srestroncio@Raidne:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686   82  Linux swap / Solaris
/dev/hda2            5100        7202    16892347+  83  Linux
/dev/hda3            7203        7296      755055    5  Extended
/dev/hda5            7203        7296      755023+  82  Linux swap / Solaris
srestroncio@Raidne:~$

---

### Post by vtel57 on 2007-05-21
I really hate to tell you this, SrEstroncio, but you don't appear to have *any* Windows on that hard drive.

> /dev/hda1 * 1 5099 40957686 82 [COLOR="Red"]Linux swap[/COLOR] / Solaris 
/dev/hda2 5100 7202 16892347+ 83 [COLOR="Red"]Linux[/COLOR]
/dev/hda3 7203 7296 755055 5 Extended
/dev/hda5 7203 7296 755023+ 82 [COLOR="Red"]Linux swap[/COLOR] / Solaris

/hda1 appears to be 40Gig /swap partition

/hda2 appears to be a 16Gig Linux partition (possibly your Ubuntu)

and

/hda5 appears to be an 800Meg /swap partition

No Windows. :(

---

### Post by SrEstroncio on 2007-05-22
oh crap.

But I still get the Start Windows XP option when I turn on my comp.
ok, assuming I messed up my ubuntu installation, seeing how my partitions are, would something happen If I format my 40GB patition (the one I thought was Windows and apparently it's a swap partion) and reinstall windows in it?

Thanks in advance

here are some screen captures:

[IMG]http://bb.1asphost.com/reipeloazul/Screenshot.png[/IMG]
[IMG]http://bb.1asphost.com/reipeloazul/Screenshot-2.png[/IMG]
[IMG]http://http://bb.1asphost.com/reipeloazul/Screenshot-3.png[/IMG]

---

### Post by vtel57 on 2007-05-22
What you're seeing when you boot up is the old Windows entry in Ubuntu's GRUB bootloader, which owns your disk's master boot record at this time.

If you install your Windows on that 40Gig partition, it will destroy Ubuntu's GRUB and place its own bootloader on the master boot record of the disk, preventing you from booting to Ubuntu again.

Don't fret yet, though... there is a way to fix that. After you've installed Windows and it has stolen the MBR from GRUB, you'll have to boot your system with the Ubuntu Live CD and repair GRUB.

There is a tutorial on this forum somewhere on how to do that, but I can't find it at the moment. Try a search here for "Restore Ubuntu's GRUB" and see what you come up with.

Keep us posted... and LUCK! :)

---

### Post by tollboy on 2008-05-21
i am using ubuntu 8.04 
and i am unable to boot vista as one of my partition id hidden 
my fstag -l output is ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b0d73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15792   126849208+  17  **Hidden** HPFS/NTFS
/dev/sda2           15793       16053     2096482+  82  Linux swap / Solaris
/dev/sda3           16054       19457    27342630    f  W95 Ext'd (LBA)
/dev/sda5   *       18277       19457     9486382+  83  Linux
/dev/sda6           16054       18276    17856184+  83  Linux

Partition table entries are not in disk order


```
cn some body help please .....

---

### Post by logos34 on 2008-05-21
> **tollboy said:**
> i am using ubuntu 8.04 
and i am unable to boot vista as one of my partition id hidden 

/dev/sda1   *           1       15792   126849208+  17  **Hidden** HPFS/NTFS[/code]

cn some body help please .....

sudo grub

grub> unhide (hd0,0)

grub> quit


Or open Gparted:

-right click sda1>'manage flags>uncheck 'hidden' box

---

