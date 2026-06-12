---
title: "Problems mounting hard drive"
date: 2012-10-16
forum: General Help
---

### Post by c-m on 2012-10-16
Running 12.04 on SSD.

I have a separate 1TB drive that split between music /dev/sdb2 and other stuff /dev/sdb4

Here is the fstab:

```
/dev/sdb2 /media/music	ext4    rw,user,exec,auto 0	0
/dev/sdb4 /media/Home	ext4    rw,user,exec,auto 0	0
```

Now on a fresh restart all works as expected. However after a random time (varies from 10mins to 10 hours), I can access /media/Home, but some of the directories appear empty, and I seem to lose permissions to delete things. If left eventually I loose all permissions for that partition.

If I unmount the partition and then re-mount it I get the following:

```
rror mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Any ideas?

---

### Post by pqwoerituytrueiwoq on 2012-10-16
i would boot a live cd and open gparted and use it to check the partition

---

### Post by c-m on 2012-10-18
Checked it with Gparted and all appears fine.

I just don't understand it. 

I lose permissions on the drive, and half it's contents vanish. 

I can't unmount it. 

If I restart the computer all is ok again.

---

### Post by Insomn1a on 2012-10-18
> **c-m said:**
> Checked it with Gparted and all appears fine.

I just don't understand it. 

I lose permissions on the drive, and half it's contents vanish. 

I can't unmount it. 

If I restart the computer all is ok again.

try removing the drive from fstab then reboot, then run this and see if it stays working.

sudo mount -t ntfs -o rw,auto,user,fmask=0022,dmask=0000 /dev/whatever /mnt/whatever

Source: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by sienile on 2012-10-18
Is the 1 TB drive also a SSD? I've heard of earlier SSDs having fragmentation errors over time. Perhaps this is your problem.

I don't own any SSDs myself, so I don't have a solution available. I do know that there are many SSD defragmentation programs (I think they refer to them as "optimization" tools.) for Windows, but I'm not sure if there are any good ones for Linux.

---

### Post by c-m on 2012-10-18
> **Insomn1a said:**
> try removing the drive from fstab then reboot, then run this and see if it stays working.

sudo mount -t ntfs -o rw,auto,user,fmask=0022,dmask=0000 /dev/whatever /mnt/whatever

Source: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

The drive is ext4

---

### Post by c-m on 2012-11-05
I've checked the partition in Gparted and all is well there.

The problem seems to occur when copying or writing files to that particular partition. 

Other partitions on the same drive are fine.

---

