---
title: "Swap Partitions"
date: 2008-06-30
forum: General Help
---

### Post by t4ggs on 2008-06-30
Hi im using ubuntu 8.04 with compiz...i have a 3.06Ghz p-IV 1Gb of ram and nvidia 6600GT..and it run very slow....even vista run faster on this pc..so i thought maybe my swap partition is not enabled...if not, what else could be??

---

### Post by Claus7 on 2008-06-30
Hello,

something that you could do very easily in order to check for yourself, should be to go to System -> Administration -> System Monitor and check, among other things, the tab processes. Does anyone of them occupy more memory or cpu than it should?

Hope this sed some light,
Regards!

---

### Post by t4ggs on 2008-06-30
not really. just swiftweasel (u know firefox) just some 90Mb and 10% of cpu...

---

### Post by t4ggs on 2008-07-01
take a look...why swap is 0%??

---

### Post by soccerboy on 2008-07-01
your swap is not enabled.  try ```
swapon
``` in the terminal

---

### Post by t4ggs on 2008-07-01
> **soccerboy said:**
> your swap is not enabled.  try ```
swapon
``` in the terminal


That's what i get:

usage: swapon [-hV]
       swapon -a [-e] [-v]
       swapon [-v] [-p priority] special|LABEL=volume_name ...
       swapon [-s]


and when i enter in gParted and right click on the swap partition i can click con swapon or swapoff...but it's still showing me 0% when opening resources at system Monitor...

any ideas why??
thanks

---

### Post by avtolle on 2008-07-01
Probably no swap is shown as being used because it isn't; you have 1 GB RAM, so the need to use the swap partition is limited. Do you have the correct driver for your graphics card installed?

---

### Post by t4ggs on 2008-07-01
yes i do... and its been used right now, it may have been what u said about my ram.. but still it run slowly...i opened two windows of firefox and a movie and the computer can barely move...and in windows i can do the same thing with out any speed issue.

i wonder why?

---

### Post by soccerboy on 2008-07-01
> **avtolle said:**
> Probably no swap is shown as being used because it isn't; you have 1 GB RAM, so the need to use the swap partition is limited. Do you have the correct driver for your graphics card installed?

If you look at the screenshot, it says there is 0 bytes of 0 bytes swap.
So no swap is available.  Do you have a swap partition?  What are contents of your fstab?

---

### Post by mbsullivan on 2008-07-01
Hi t4ggs,

Is the swap drive listed under:

```
sudo fdisk -l
```

???

If it turns out you have no swap drive, you can always use a swap file (the speedup from having a separate partition has become negligible). See [this page]("https://help.ubuntu.com/community/SwapFaq") for help making a swap file.

> Do you have the correct driver for your graphics card installed?

This is another thing which could make your computer seem painfully slow... What does it say for the Driver section of your video card device under /etc/X11/xorg.conf ??? Also, do you have nvidia-glx installed?

Mike

---

### Post by t4ggs on 2008-07-02
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           27135       32301    39062520   83  Linux
/dev/sdb2   *           2       27134   205125480    5  Extended
/dev/sdb5               2       25408   192076888    7  HPFS/NTFS
/dev/sdb6           25409       26656     9434848+   7  HPFS/NTFS
/dev/sdb7           26657       27134     3613648+  82  Linux swap / Solaris

I have a swap partition, but when entering gparted after reboot i have to turn it on, dont know why it happens.. after that in system monitor it says 0 bytes of 3.4 Gb

i think it makes swapoff alone...

/etc/X11/xorg.conf:


Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection



i have nvidia-glx-new

---

### Post by Slim Odds on 2008-07-02
Well.... for one thing, your system is only using 41% of your RAM. If your system is slow, it's not because there is no swap used.

---

### Post by soccerboy on 2008-07-02
is you system slow all the time?  if not, is that screenshot from when your system was slow?

---

### Post by t4ggs on 2008-07-02
hehehe i dont know why but now i opened the same programs i had before and its not slow...anyway u r right that if it is using 41% of my ram it doesnt need the swap, but still why after reboot the swap turns off alone??

is this automatically??

---

### Post by t4ggs on 2008-07-06
anyone knows why my swap partition turn off alone?? its always turned off...when i turn it on, after reboot it is off again.

---

### Post by Juhla Mokka on 2008-07-08
Hi, I am not sure if my swap partition is working properly. Here is what the FAQ ([https://help.ubuntu.com/community/SwapFaq#Troubleshooting](https://help.ubuntu.com/community/SwapFaq#Troubleshooting)) told me to do:
```
root@Frog:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7fcef8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         702     5632000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         702         893     1536000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3             893       18183   138880000    7  HPFS/NTFS
/dev/sda4           18184       19457    10233405    5  Extended
/dev/sda5   *       18184       19397     9751423+  83  Linux
/dev/sda6           19398       19457      481918+  82  Linux swap / Solaris
root@Frog:~# free
             total       used       free     shared    buffers     cached
Mem:       2066664     913560    1153104          0      67792     339672
-/+ buffers/cache:     506096    1560568
Swap:       481908          0     481908
root@Frog:~# swapoff -a
root@Frog:~# /sbin/mkswap /dev/sda6
Setting up swapspace version 1, size = 493477 kB
no label, UUID=0aa0000f-617c-45a4-9a2e-647352f5a4cb
root@Frog:~# swapon -a
swapon: /dev/sda6: Device or resource busy

```

So what does the last line mean? Did it work properly or not? System monitor does not show any use, even I have started many programs - up to 41% of memory being used.

---

### Post by t4ggs on 2008-07-08
no idea men im still having trouble with my swap partition...think i'll have to format/.

---

