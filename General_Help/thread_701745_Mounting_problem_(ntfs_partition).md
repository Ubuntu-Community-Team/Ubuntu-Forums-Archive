---
title: "Mounting problem (ntfs partition)"
date: 2008-02-19
forum: General Help
---

### Post by stcninja on 2008-02-19
Okay, so I'm still having issues with my dual boot system. First off I had problems with my GRUB, and then later found out that my partition table was messed up. So, I got Knoppix LIVE and ran that, ran gpart and got repeatedly the same correct looking partition table and wrote it.

I'm now able to access my Ubuntu partition. I can't however load up my NTFS partition. I get this error message:

> Failed to read last sector (301170491): Invalid argument
Perhaps the volume is a RAID/LDM but it wasn't setup yet, or the
wrong device was used, or the partition table is incorrect.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

So I'm thinking that possibly gpart got the last sector of that partition wrong and that's what is giving me my problems. I've tried to manually mount it (as in through the terminal) with using both:

sudo mount -t ntfs /dev/sda1 /media/sda1

and

sudo mount -t ntfs-3g /dev/sda1 /media/sda1

but gives me the same error message. I also used:

> ntfsresize --info --force /dev/sda1

to get more information about my partition. (not actually resizing mind you, just getting information i need)

here's the printout:

> ntfsresize v1.13.1 (libntfs 9:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 154199290368 bytes (154200 MB)
Current device size: 154199289856 bytes (154200 MB)
Checking filesystem consistency ...
Cluster 1989 is referenced multiply times!
Cluster 13592 is referenced multiply times!
Cluster 21781990 is referenced multiply times!
Cluster 21781991 is referenced multiply times!
Cluster 21781992 is referenced multiply times!
Cluster 21781993 is referenced multiply times!
Cluster 21781994 is referenced multiply times!
Cluster 21781995 is referenced multiply times!
Cluster 21781996 is referenced multiply times!
Cluster 21781997 is referenced multiply times!
100.00 percent completed
ERROR: Filesystem check failed!
ERROR: 818 clusters are referenced multiply times.
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

So, from comparing the volume size to the device size it looks like it's off by about 1 secor. I don't know what the other stuff is though but it doesn't look good =X and my windows is messed up so I can't do the command it's asking me to perform. (trying to fix windows was actually the source of my problems in the first place...yeah, lame.)

So I'm at a lost about where to go next with this. Basically, I just want to get that parition mounted so that I can get my data off onto external media and then I can reformat my entire computer and get a clean start.

Thanks for your help!
~STCninja

---

### Post by fjgaude on 2008-02-21
The problem I'm having with your setup is how the partition table got messed up in the first place?

Seems like gpart could have caused troubles, but OTOH it could be simply a drive with clusters unallocated or allocated wrongly.

Using Windows CHKDSK could fix the partitions and clusters. It's all up to you which way you go.

---

### Post by stcninja on 2008-02-22
honestly if I knew I would tell you. And if I could go into Windows I would.

I have a dual boot system on the same harddrive. 150GB ntfs partition and a 10GB Lunix partition. I primarily used windows until it messed up a while ago and so I switched to using solely Linux. Then recently I had gotten an XP cd from my neighbor so that I could fix my windows OS (why? I don't know why, I don't even need Windows but I tried fixing it anyways). I went to go start up the installer hoping that it'd give me the option to just reinstall the OS instead of having to do a full format. but it said that it didn't recognize the NTFS partition for some reason. So I quit. I reboot. And my GRUB does not come up. So I start up from a LIVE disk and run an fdisk -l and what it gives back to me was not my partition table. Basically showing that there was no partition table. So I ran gpart through Knoppix a few times to see what it guessed a few times. It looked accurate as far as I could remember. And I wrote it. I could start seeing my Linux partition, so I fixed GRUB, rebooted and i have my LINUX partition up and running but the NTFS one is still not working.

Had my partition table not beed messed up, I wouldn't have run gpart. And like I said in the original post, I cannot run windows so I cannot run CHKDSK

---

### Post by fjgaude on 2008-02-22
The only thing left is to use Gparted which may be installed already in your Ubuntu partition. You can boot into it and see: System / Administration / Partition Editor.

If it's not there simply apt-get install it:

```
sudo apt-get install gparted
```

Gparted handles nfts file systems nicely. In there do a Check of the unmounted partition. If you can do that it will repair the partition. If not, I'm out of suggestions.

Good luck!

---

