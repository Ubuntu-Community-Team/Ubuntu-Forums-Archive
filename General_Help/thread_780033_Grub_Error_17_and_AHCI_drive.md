---
title: "Grub Error 17 and AHCI drive"
date: 2008-05-03
forum: General Help
---

### Post by tvg on 2008-05-03
I use Vista, 1st partition. The second one (primary) is ext3 with Ubuntu and the third one is Ubuntu swap.

Ubuntu Hardy DVD latest version.

Total HDD drive is 320 mb (30000.... bytes).

I installed Vista with AHCI, works well.
I installed Ubuntu with AHCI, works well too (until reboot).

Grub does not seem to support AHCI drive: it cannot boot from it, falling back with "Error .... 17". I cannot figure out what description of this error means.

When I turn off AHCI in bios, Grub boots well Ubuntu and Vista.

As I understand, Grub is very buggy and outdated bad software, but is there any solution to keep AHCI and still boot Ubuntu (and Vista too)? May be I should work with Vista loader, which have to load Ubuntu? Thanks.

---

### Post by quad65 on 2008-11-23
I have the same problem. No solution?

---

### Post by meierfra. on 2008-11-23
If your bios allow you, try switching from "AHCI" to "RAID" mode (the RAID mode also enables "AHCI")

---

### Post by rbmorse on 2008-11-23
Grub (and Linux) work fine with AHCI controllers. 

The easiest fix is to boot from the Ubuntu Desktop CD or SystemRescueCD or some other Linux LiveCD.  Once that is running, open a terminal and do the following:

sudo grub
find /boot/grub/stage1

The find command will return a value in the form of 

(hdX,y) 

Grub enumerates things starting at zero, so from your description of the disk layout, it should return  (hd0,1) which translates as the second partition on the first hard drive.  In any case, take the value returned from the find command and at the terminal (stll at the grub prompt) enter

root (hdX,Y)  

where X and Y are the results from the find....say root (hd0,1).  Syntax is critical here so watch for extra spaces and make sure the comma separated the two values really is a comma. 

Then enter 

setup (hd0)

This will rewrite the Master Boot Record on the hard drive. It should return some status information that  you can ignore as long as no errors are reported. 

Reboot

---

### Post by quad65 on 2008-11-23
> **meierfra. said:**
> If your bios allow you, try switching from "AHCI" to "RAID" mode (the RAID mode also enables "AHCI")

Can I use RAID mode without actually RAID'ing HDDs?

rbmorse; I'm gonna try that.

---

### Post by quad65 on 2008-11-23
Alright, I've done what you've told. I believe I did everything right, because now I get an Error 18. :)

As far as I understand, this is related to BIOS limitation and I have to make a separate /boot partition.

I can create a partition, but which filesystem should it be and how do I mount it as /boot?

Thanks for your help.

---

### Post by meierfra. on 2008-11-23
> Can I use RAID mode without actually RAID'ing HDDs?

Yes, you can.

Try that  before creating a separate boot partition:

Do you get Grub Error 18 before the Grub menu appears?

How old is your computer?

Are you still able to boot into Ubuntu by disabling "AHCI" in the bios?

Before creating the separated boot partition, lets do some checks:
Boot into Ubuntu (or boot the Ubuntu LiveCD, if you can't boot into Ubuntu)

In a terminal:
```
sudo fdisk -lu

sudo grub
```

and at the grub prompt

```
find /boot/grub/stage1 
```
This will return "(hdX,Y)", where X and Y are some numbers, for example "(hd0,1)"  (Sorry for repeating this, but if you boot from the LiveCD and you have more than one disk, you might get a different answer than the last time)
Use whose numbers in the next line: (still at the grub pompt)
```

blocklist (hdX,Y)/boot/grub/stage2
blocklist  (hdX,Y)/boot/grub/menu.lst
quit
```

Post the output of all these commands.


Instruction to create a separate boot partition:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition")

---

### Post by quad65 on 2008-11-24
I get Error 18 just after `Grub Stage 1.5 loading` message. Menu does not appear.

My computer is fairly new. I have a Gigabyte GA-M78GM-S2H mainboard that comes with AMD 780G chipset. And AMD X2 4800+ processor and 4GB RAM. Actually, my old mobo had problems with Linux so I bought this rig in order to be able to use Ubuntu.

Tried RAID mode, no success.

Here is the part with outputs:

```

sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000123b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   245762047   122880000    7  HPFS/NTFS
/dev/sda2       245762370  1250258624   502248127+   f  W95 Ext'd (LBA)
/dev/sda5       245762433  1209308939   481773253+   7  HPFS/NTFS
/dev/sda6      1209309003  1213517969     2104483+  82  Linux swap / Solaris
/dev/sda7      1213518033  1229791814     8136891   83  Linux
/dev/sda8      1229791878  1250258624    10233373+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2af92af8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625137344   312568641    7  HPFS/NTFS

```

```

grub> find /boot/grub/stage1
 (hd0,6)

grub> blocklist (hd0,6)/boot/grub/stage2
(hd0,6)9732096+96,9732200+142

grub> blocklist (hd0,6)/boot/grub/menu.lst
(hd0,6)9748496+10

grub> 

```

---

### Post by quad65 on 2008-11-24
Hello,

I would like to let you know that I created a separate boot partition and reinstalled Ubuntu. No problems so far.

Thank you all for your guidance.

---

