---
title: "Grub doesn't recognize windows partition?"
date: 2008-04-05
forum: General Help
---

### Post by fearnloathing55 on 2008-04-05
I recently installed Ubuntu on my home computer as my first ever linux distro and it's been working wonderfully. My only problem is that I can no longer boot into windows XP. 

df returns this-

/dev/hda1             15116836  13964848    384084  98% /
varrun                  517304       104    517200   1% /var/run
varlock                 517304         0    517304   0% /var/lock
udev                    517304        92    517212   1% /dev
devshm                  517304         0    517304   0% /dev/shm
lrm                     517304     16488    500816   4% /lib/modules/2.6.22-14-generic/volatile
/dev/hda3              9284512         8   9284504   1% /windows
/dev/sda1            244196000 110823432 133372568  46% /media/FreeAgent Drive


The problem is Windows is on hda5, not hda3 (which is an essentially empty FAT32 partition). All of my files are still there, because if I go to the File Browser they show up under the name "80 GB Volume" in the side bar. (it's an NTFS partition). 

Menu.lst looks like this-

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=776d39e5-3334-4308-8b64-4bf4f2c26ece ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=776d39e5-3334-4308-8b64-4bf4f2c26ece ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP Professional
root		(hd0,5)
makeactive
chainloader	+1

If I select the windows option at start up Grub returns the error "Device not recognized." I'm a complete linux n00b (obviously) so I'm not sure what I need to do to get Grub to boot from a partition it doesn't seem to acknowledge exists. . .

---

### Post by logos34 on 2008-04-05
> **fearnloathing55 said:**
> 
The problem is Windows is on hda5, not hda3 (which is an essentially empty FAT32 partition). All of my files are still there, because if I go to the File Browser they show up under the name "80 GB Volume" in the side bar. (it's an NTFS partition). 

....

title		Windows XP Professional
root		(hd0,5)
makeactive
chainloader	+1

If I select the windows option at start up Grub returns the error "Device not recognized."

If it's hda5, then menu.lst entry should read:

> root		(hd0,**[COLOR="Red"]4[/COLOR]**)

---

### Post by fearnloathing55 on 2008-04-05
Changed, still get the same error. "Invalid Device requested"

The only time I don't get that error is if I try to boot from hd3, but then it just tells me that it didn't detect and operating system (for good reason, because there isn't one).

---

### Post by logos34 on 2008-04-05
Post output of
[B]
sudo fdisk -l[/B]

(By the way:  your ubuntu root is 98% full--better do something about that and clear some room or you may be unable to boot into linux as well)

---

### Post by fearnloathing55 on 2008-04-05
Ok, so fdisk -l gives me 

>  Device Boot      Start         End      Blocks   Id  System
/dev/hda1                       1        1912    15358108+  83  Linux
/dev/hda2                    1913     12572    85496450    f  W95 Ext'd (LBA)
/dev/hda3   *                12572   13729     9293602+   b  W95 FAT32
/dev/hda5                    1913     12514    85030533+   7  HPFS/NTFS
/dev/hda6                    12515   12572      465853+  82  Linux swap / Solaris



Something got screwed up somewhere, because that doesn't even make sense.  It looks like it's reading the same partition twice (as hda2 and hda5).

This is what I see in cfdisk when I try to change the boot flag to hda5 (it doesn't seem to like it when I try to do that though) -  

> Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    hda1                    Primary   Linux ext2                       15726.74 
    hda5                    Logical   NTFS             []              78303.30
    hda6                    Logical   Linux swap / Solaris               477.07
    hda3        Boot        Primary   W95 FAT32                         9516.65



(oh, and 98% full was just temporary, it's back down to 50% now. . .)

---

### Post by logos34 on 2008-04-05
> **fearnloathing55 said:**
> 
Something got screwed up somewhere, because that doesn't even make sense.  It looks like it's reading the same partition twice (as hda2 and hda5).

No, actually it looks fine.  (Think of the extended partition hda2 as just a wrapper containing the two logical partitions, / and /swap)

> This is what I see in cfdisk when I try to change the boot flag to hda5 (it doesn't seem to like it when I try to do that though) -  

Try using gparted:

sudo gparted

>right-click on hda5>manage flags>check **boot**

remove boot flag on the other one

---

### Post by fearnloathing55 on 2008-04-06
Tried thatt, still doesn't work though. Gparted says that the problem is that it's "unable to read the contents of this filesystem." Even though I can access the files just fine from the file browser:confused:

---

### Post by logos34 on 2008-04-06
Hmm...Maybe the partition table needs fixing.  There's a tool for that:

sudo apt-get install testdisk

sudo testdisk

Or if you have an XP install disc you could try running error check on it (althought the fact that you can read it means this is probably not the issue).  Boot into the recovery console (>'R').  At the prompt run **chkdsk /r**

---

