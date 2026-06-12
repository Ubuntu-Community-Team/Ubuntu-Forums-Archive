---
title: "Able to mount but unable to write"
date: 2005-10-23
forum: General Help
---

### Post by Incendium on 2005-10-23
Hey there. I am having problems writing to my mounted FAT32 drive.

I currently have 3 drives - 2 IDE, a 60GB FAT32 (Primary Master) and a 40GB NTFS (Primary Slave); 1 SATA, a 60GB Ext3 (This has ubuntu installed). I am able to mount the FAT32 drive using the method provided in the guide at ubuntuguide.org. I can read the drive, but cannot write to it. I get a no permission error, more or less.

Does anyone have any suggestions as to what I might try next, or what could be wrong?

---

### Post by SilentCacophony on 2005-10-23
Hi. There could be a number of things wrong. The most common problem that I notice with this, is that if you are trying to change permissions on an already mounted partition, you usually need to unmount it before re-mounting with new options in order for them to immediately take effect.

Anyway, it would be easier to diagnose the problem if you posted the output of these commands, run from the terminal:

**cat /etc/fstab**

**mount**

**ls -la /media**

(Assuming that you mounted it within a subfolder in /media)

---

### Post by mlgg on 2005-10-24
Hi!

In your /etc/fstab, you should have a line like this to be able to write:

/dev/partitionFAT32 /mnt/mountingpoint auto rw,uid=youuid,gid=yourgid 0 0 

Hope that's work

---

