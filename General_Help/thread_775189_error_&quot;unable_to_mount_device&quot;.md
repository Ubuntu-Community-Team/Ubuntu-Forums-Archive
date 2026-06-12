---
title: "error &quot;unable to mount device&quot;"
date: 2008-04-29
forum: General Help
---

### Post by road_rage on 2008-04-29
I have been running gusty on a signle sata drive and everything has been working. Tonight I added two additional drives both pata one is jumped master and the other slave. After booting my system and logging into my desktop I launched file manager and attempted to access the newly added drives which appeared in the left pane. When I click to access the drive I am getting a pop-up message stating "The volume "XXXX_XXX" is not mounted. Do you want to mount it?" when I click "yes", I get another message stating "Unable to mount device". 

After googling a bit I decided to run GParted to see if the drives were recognized there and what I could gather for info. It does recognize both drives, /dev/sdb1 and /dev/sdc1 and shows each has a file system as ext2 and reports the correct size but still will not allow me to mount them ?

I am unsure as to what I have on the drive so my primary goal right now is to preserve the drive and be able to mount it. 

TYIA,
--RR 

Here is a sudo fdisk -l:
```
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3b0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17864   143492548+  83  Linux
/dev/sda2           17865       18241     3028252+   5  Extended
/dev/sda5           17865       18241     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4a9f2ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033632   83  Linux

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc9e53e90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36481   293033632   83  Linux
```

---

### Post by tamoneya on 2008-04-29
Try one drive at a time.  Try different IDE channels.  Try putting them on Cable Select instead of master and slave.

---

### Post by road_rage on 2008-04-30
> **tamoneya said:**
> Try one drive at a time.  Try different IDE channels.  Try putting them on Cable Select instead of master and slave.

I tried all of the above. When I have the one master on the channel alone and set to master it has some weird hw conflict with the sata master and the system takes forever to boot. I removed that drive and I am now running with a single drive alone and set to master. The system then booted fine, but although the drive is appearing I am still getting the same errors when trying to access/mount ?

```
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3b0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17864   143492548+  83  Linux
/dev/sda2           17865       18241     3028252+   5  Extended
/dev/sda5           17865       18241     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc9e53e90

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033632   83  Linux

```

---

### Post by Ziggy72 on 2008-04-30
Try this:

As root, make the directories /media/sdb1 and /media/sdc1.

As root, edit /etc/fstab and add the following:
```

# /dev/sdb1
/dev/sdb1	/media/sdb1	ext2    defaults	 0       2
# /dev/sdc1
/dev/sdc1	/media/sdc1	ext2    defaults	 0       2

```

Then try mounting using:
```
 sudo mount -a 
```

If that works, the new disks will remount at each boot. If it doesn't work, just remove the fstab entries you created. Good luck:)

---

### Post by road_rage on 2008-04-30
> **Ziggy72 said:**
> Try this:

As root, make the directories /media/sdb1 and /media/sdc1.

As root, edit /etc/fstab and add the following:
```

# /dev/sdb1
/dev/sdb1	/media/sdb1	ext2    defaults	 0       2
# /dev/sdc1
/dev/sdc1	/media/sdc1	ext2    defaults	 0       2

```

Then try mounting using:
```
 sudo mount -a 
```

If that works, the new disks will remount at each boot. If it doesn't work, just remove the fstab entries you created. Good luck:)

That worked like a champ, thanks. 

Just curious, is this something I need to do for each disk I add ? If I transfer the data off the drives and recreate and present the partition will that allow them to mount without adding to my fstab manually each time ?

--RR

---

### Post by Ziggy72 on 2008-04-30
For each disk you want to mount at boot, you need the correct folder in /media and a valid entry in /etc/fstab.

---

