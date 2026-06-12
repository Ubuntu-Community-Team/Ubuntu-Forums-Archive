---
title: "Press S to skip or M for manual recovery"
date: 2014-04-13
forum: General Help
---

### Post by the.z.cuber on 2014-04-13
Yes, I tried looking this up. 

I just removed Mint from a dualboot, and refreshed grub. Ubuntu now goes to the splash screen, before saying press S to skip...that one. If I skip, there are 3 things I skip, the latter 2 giving me the option to continue by waiting. It then brings me to the terminal (the black screen, it has nothing in it). From there is where I am stuck. The message before the first skip prompt is that there is an error mounting /. 

I have a live USB and can use it, but there is no internet on it (I do not think I need it for this anyway). 

Any and all help is appreciated. Thanks!

---

### Post by Double.J on 2014-04-13
Hi there!

Sorry to hear about the problem. Since you didn't make any changes to the actual system having the issue, but removed another OS and jut reconfigured the Bootloadet, it is most likely that the problem is the partition list in /etc/fstab no longer matches the drive layout.

To see your current partitions
```
sudo fdisk -l
```
To see the UUID of the partitions
```
blkid
```
Finally to see the contents of /etc/fstab in terminal:
```
sudo cp /etc/fstab /etc/fstab.bak && sudo nano /etc/fstab
```

Main things to look for is changed UUID or /dev/sdx number between the record in fstab and your current partitions.

Hope it helps!

Jj

---

### Post by the.z.cuber on 2014-04-14
All it shows is this:
```
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

I believe this is for the live USB. However, when I navigate by hand to /etc in the HDD, there is only a fstab.d folder, which is empty.

---

### Post by Double.J on 2014-04-14
Oh dear,

Well let's make sure we have the correct read/write partitions to be double sure. (fstab.d is a folder. there's most likely nothing in it, so that shouldn't be a problem in itself!
From the live cd use
```
sudo fdisk -l
```to double check which partition the ubuntu iroot partition nstall is on.

Then lets make a mount point for ubuntu's root partition and remount it there:
```
sudo mkdir /media/ubuntu
sudo mount -o remount,rw /dev/sdxy
``` where x is the hard drive letter (most likely a or b) and y is the partition number of the root partition.

Then let's try to backup and open fstab one last time:
```
sudo cp /media/ubnutu/etc/fstab /media/ubuntu/etc/fstab.bak
sudo nano /media/ubuntu/etc/fstab
```

if we still can't find the fstab, it can be rebuilt without much difficulty, however there's no really anything that should delete it in the first place, so please let us know how you get on!

Jj

---

### Post by the.z.cuber on 2014-04-14
I just found the file by hand. It is /media/ubuntu/Ubuntu/etc/fstab

It shows 2 UUIDs, the second of which is the one from fdisk -l

Should I comment out the first UUID?

---

### Post by Double.J on 2014-04-14
Hi there, sorry busy day!

hmm i would say not to comment out. 

By default there should be at least two; one showing where swap is and one where root is. If you have a seperate /home or /boot partition that should also be in there. 

Are all your system partitions listed abd do all the uuid's /dev/sd partition numbers match? Fdisk's output?

Jj

---

### Post by the.z.cuber on 2014-04-14
Yes, it is the sole partition on my HDD, and the UUID matchrs.

---

### Post by Double.J on 2014-04-15
Hmm, well if the fstab for the system is correct, and you've updated the bootloader, I'm out of ideas I'm afraid. Whenever I've had these issues this has been the cause.

All i can suggest is to run fsck on the partition, try older kernels and run boot repair. Sorry I can't be more help.

Jj

---

### Post by the.z.cuber on 2014-04-15
I just realised I deleted all partitions except for sdb5 (the Ubuntu one). I tried a fresh install of grub to no avail. Could the deleted partition be the key?

---

### Post by the.z.cuber on 2014-04-27
I'd like to bump this. I think it is the deleted partition(s), but am not sure. Is there any way to restore the previous partitions without doing a complete reinstall of Ubuntu?

---

### Post by linuxonbute on 2014-04-27
I am not sure if I understand exactly what you did so perhaps if you answer these questions I might.

When you say you end up at a black screen with nothing on it do you mean literally nothing or do you get the normal prompt as in a terminal?

When you ran update-grub had you done it from that screen or was it from when you booted from DVD?

---

### Post by the.z.cuber on 2014-04-28
Just black, not the basic terminal. I presume it's because the data failed to load, so it it showing what it has (nothing). 

I ran update-grub from the live disc (USB)

---

