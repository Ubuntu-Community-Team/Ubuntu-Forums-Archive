---
title: "Cannot make Win partition bootable"
date: 2008-05-19
forum: General Help
---

### Post by ac7 on 2008-05-19
Hi all,
Alright, I have very uncommon problem, I will tell you all specifics


1. I have HP TC4400 tablet pc  (i.e. no cd/floppy drive)

2. I originally had windows, on my 40 GB hard disk ( Got with tablet originally)

3. Just recently I upgraded my hard drive to 160GB

4. I installed Ubuntu using my external usb hard drive. It runs perfectly fine.

5. I had made a image of old windows partition from old hardisk and restored it on D: (/dev/sda2) on new one [using **partimage** program, i.e. It copies all boot records exactly as it were before]

[the reason I cannot restore on C: i.e. /dev/sda1, the 160GB drive is too big for the BIOS on my laptop, so I needed to keep /boot on C: i.e. within some megs of starting of drive, otherwise, Ubuntu was not running]

6. [COLOR="Red"]The problem is[/COLOR], when first time I restored my windows partition at C: it works as it was before, but when I restored on D: although ubuntu has automatically made a entry for windows os in **menu.lst**. BUT, as soon as I am selecting the "Windows" it is hanging and no HDD Led or any activity is going on. 

I really need my old Windows partition and this new Ubuntu, I don't intend to compromise on either.
[B][COLOR="Red"]
PLEASE help!
[/COLOR][/B]
Here are some more details


```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2f6dfb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         102      819283+  83  Linux
/dev/sda2   *         103        7751    61440000+   7  HPFS/NTFS
/dev/sda3            7752       14762    56315857+   7  HPFS/NTFS
/dev/sda4           14763       24321    76782667+   5  Extended
/dev/sda5           14763       21392    53255443+   7  HPFS/NTFS
/dev/sda6           21393       24194    22507033+  83  Linux
/dev/sda7           24195       24321     1020096   82  Linux swap / Solaris


```

sda1 has /boot
sda6 has /
sda2 has windows

Please let me know if you need more details or clarifications.

Thanks in advance

---

### Post by roe_polak on 2008-05-19
What does your menu.lst look like?

---

### Post by ac7 on 2008-05-19
I am  copy and pasting the stanza of interest here:


```

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=702734bb-6f11-4e7b-b5b1-2544436b9958 ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=702734bb-6f11-4e7b-b5b1-2544436b9958 ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

---

### Post by logos34 on 2008-05-19
You definitely need to edit **boot.ini** to point to new location:
> 
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)**partition([COLOR="Red"]2[/COLOR])**\...
[operating systems]
multi(0)disk(0)rdisk(0)**partition([COLOR="Red"]2[/COLOR])**\...

Whether that alone will solve the problem I don't know

---

### Post by ac7 on 2008-05-19
should I suspect my windows boot sector got corrupted or need fix?

---

### Post by logos34 on 2008-05-19
[duplicate]

---

### Post by ac7 on 2008-05-19
> **logos34 said:**
> You definitely need to edit **boot.ini** to point to new location:


Whether that alone will solve the problem I don't know

thanks for suggestion

but I had done that already, it didn't solve the problem.

---

### Post by logos34 on 2008-05-19
maybe run **fixboot** from xp install cd recovery console

---

### Post by ac7 on 2008-05-19
> **logos34 said:**
> maybe run **fixboot** from xp install cd recovery console

I will see if I can arrange a cd rom drive.

There is no way doing it or analyzing what EXACTLY is going on from Ubuntu itself?


I don't have much knowledge how MBRs works, does each partition has it's own? Because the old win Image has MBR copy too with itself, which I restored on D. (/dev/sda2)

---

### Post by logos34 on 2008-05-19
> **ac7 said:**
> I will see if I can arrange a cd rom drive.

oops, forgot you have no optical drive
> 
There is no way doing it or analyzing what EXACTLY is going on from Ubuntu itself?

I don't have much knowledge how MBRs works, does each partition has it's own? Because the old win Image has MBR copy too with itself, which I restored on D. (/dev/sda2)

You could try flagging windows partition in ubuntu for **chkdsk** on reboot (you can't run a disk check from linux itself)

sudo apt-get install ntfsprogs

sudo ntfsfix

I'm fresh out of ideas

---

### Post by ac7 on 2008-05-20
:) well, you are late. I already got it fix using an alternate method. But thanks though.

I will explain for someone else who might face similar problem.

Actually I resized all the partitions, I made the first partition 40GB and put the boot just after that, because my BIOS can read boot sector till 60GB or something.

And I restored my windows in C: 

:) EVERYTHING works fine.

But still, it would be good learning thing if we could know WHY it didn't work on D:.

Thanks a lot.

---

### Post by ali999 on 2008-05-20
I have had issues with changing windows partitions around before. I think its something to do with where windows installs its boot loader. It is possible that the windows boot system is still looking for windows to be in a drive called C:/. My solution is to enable ntfs in your ubuntu so you are able to backup your stuff and then do a fresh install of windows. Maybe not the best but it works.

---

