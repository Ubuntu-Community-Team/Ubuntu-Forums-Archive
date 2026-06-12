---
title: "Recurring Error 17 grub loader."
date: 2008-05-27
forum: General Help
---

### Post by MissMachine on 2008-05-27
From my understanding, this error is common when the BIOS stores different information about your hard drives than what is loaded on boot by GRUB. I have been able to fix the error by editing the /grub/device.map and /menu.lst files to trick it into mounting and booting the correct HDD. However, every time I install updates, it causes those files to revert back to how they were. I have to boot up a liveCD to edit those files every this happens, and it's getting to be pretty annoying. 

So basically, I'm asking you, my trusty Ubuntu tech support, what is the long term remedy to my problem? Thanks!

---

### Post by unutbu on 2008-05-27
Without seeing the output of ```
sudo fdisk -l
``` and an example of menu.lst before and after an update, it's hard to say for sure what the fix is.

However, if I had to venture a blind guess, I'd say perhaps groot has not been set to the partition contaning your /boot.

See [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto). Go to the section entitled "Automagic Kernels List".

---

### Post by meierfra. on 2008-05-27
> I'd say perhaps groot has not been set to the partition contaning your /boot.

I agree.

Just open up menu.lst

Look at the lines

#groot (hd?,?)

and 


title ubuntu ...
root (hd?,?)

Change the numbers in the "#groot" line to match the number in "root "line.


During a kernel update, the installer runs the program "update-grub". "update-grub" uses "#groot" to determine what "root" is supposed to be.

If you like to experiment, do "sudo update-grub" before you fix the "#groot" line. You will see that all the "root" numbers in menu.lst  are wrong. Fix "#groot" and run "sudo update-grub" and all the numbers will be correct again.

---

### Post by MissMachine on 2008-05-28
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13781378

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38913   210170362+   7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02f802f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       17495   140528556   83  Linux
/dev/sdb2           17496       18241     5992245    5  Extended
/dev/sdb5           17496       18241     5992213+  82  Linux swap / Solaris

Disk /dev/sdc: 1026 MB, 1026555392 bytes
129 heads, 16 sectors/track, 971 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes
Disk identifier: 0x38b72bb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         972     1002487+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(977, 128, 16) logical=(971, 52, 15)

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       26516   212989738+   7  HPFS/NTFS
/dev/sdd2           26517       30401    31206262+   7  HPFS/NTFS

```

This is what comes up from fdisk. 

And here is the menu.lst looks like after an update.( I double checked device.map and it turns out that was unchanged)

```
## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,0) 

```

```
## ## End Default Options ## 

title		Ubuntu 7.10, kernel 2.6.22-14-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=020c263c-ed84-4097-a368-40db0ef842c0 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic 
quiet 

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=020c263c-ed84-4097-a368-40db0ef842c0 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic 

title		Ubuntu 7.10, memtest86+ 
root		(hd1,0) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST
```

After I change the root on the "End Default Options" all to (hd0,0), the error goes away and I can boot normally. But still, anytime I get updates and restart, menu.lst reverts back to what you see up above, thus causing ubuntu not to boot.



Here is the code from device.map
```

(hd0)	/dev/sdb
(hd1)	/dev/sda
(hd2)	/dev/sdc

```

Thanks for the help.

---

### Post by VMC on 2008-05-28
> **MissMachine said:**
> 

Here is the code from device.map
(hd0)	/dev/sdb
(hd1)	/dev/sda
(hd2)	/dev/sdc

Linux is on /dev/sdb, that's why (hd1,0) didn't work. And apperantly when you you upgrade that gets changed for some reason. 

I wonder why sdb and sda are shown in reversed order. Shouldn't sda be hd0? 
Also what happened to sdd. It doesn't show up in device map.

---

### Post by meierfra. on 2008-05-28
That is very weird.   You didn't  change "#groot"? Has it always been (hd0,0)?

 Try this, change (hd1,0)  to (hd0,0). (Although  I assume you already have done that).  Then run

```
sudo update-grub
```

and see what happens.

---

### Post by meierfra. on 2008-05-28
Don't worry about the device.map. It does no get used.

---

### Post by MissMachine on 2008-05-28
> **meierfra. said:**
> That is very weird.   You didn't  change "#groot"? Has it always been (hd0,0)?

 Try this, change (hd1,0)  to (hd0,0). (Although  I assume you already have done that).  Then run

```
sudo update-grub
```

and see what happens.

Ran update-grub. It did not change anything in menu.lst, so maybe this has taken care of the problem. I'll give it a couple restarts and install some package updates and see if it holds up.

---

### Post by meierfra. on 2008-05-28
> Ran update-grub. It did not change anything in menu.lst, so maybe this has taken care of the problem.

?????  This only shows that "update-grub" is not the culprit.  Or did  you change #groot (hd1,0)"  to #groot (hd0,0) sometime today?

---

### Post by unutbu on 2008-05-28
According to [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

> The relevant parts of menu.lst that update-grub looks at are the ones in between the "### BEGIN AUTOMAGIC KERNELS LIST" and "### END DEBIAN AUTOMAGIC KERNELS LIST" lines.

Notice that you boot stanzas come before the 
"### END DEBIAN AUTOMAGIC KERNELS LIST" line.

```
## ## End Default Options ## 

title		Ubuntu 7.10, kernel 2.6.22-14-generic 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=020c263c-ed84-4097-a368-40db0ef842c0 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic 
quiet 

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
root		(hd1,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=020c263c-ed84-4097-a368-40db0ef842c0 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic 

title		Ubuntu 7.10, memtest86+ 
root		(hd1,0) 
kernel		/boot/memtest86+.bin 
quiet 

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I wonder if you simply move the 
"### END DEBIAN AUTOMAGIC KERNELS LIST" line above those boot stanzas, if update-grub will simply stopping mucking with them.

---

