---
title: "Can't read my HDD"
date: 2005-05-12
forum: General Help
---

### Post by Nissemand on 2005-05-12
I hope this is the right place to post (:
Yesterday, i was running Fedora on my HDD which i will call A. A was master and i had no other HDDs. Everything worked fine.
Then i decided to install Ubuntu. To minimize any possible lost of data, i found another HDD for now called B.
Before i install Ubuntu, i set B to master and A to slave.
I install Ubuntu, and everything seems to work fine. Or it seems to do. But i can't mount the big partition on A, only the first one, the boot partition.

What i did was:
root@noclaf:/# **mount /dev/hdb2 /mnt/hdd**
mount: either is /dev/hdb2 already mounted or /mnt/hdd is busy
                         ### hmm... i never mounted hdb2... i'll try to unmount it...
root@noclaf:/# **umount /dev/hdb2**
umount: /dev/hdb2: not mounted
                         ### okay, so it must be the dir thats the problem...
root@noclaf:/# **mount /dev/hdb1 /mnt/hdd**
                         ### okay no errors, seems to work well... hmm...
root@noclaf:/#ls /mnt/hdd
                         ### i see a list of files from my old boot partition...

So i shutdown the computer, maybe something in A crashed. I remove power from B, just to make sure everything is as it used to be, and set A to master. I turn on my computer again, and everything works as it did yesterday morning...

I hope someone here will try to help me out.

---

### Post by nad on 2005-05-12
What type of file system is fedora installed in? Did you jumper the drives correctly and/or make the right connections to the ribbon cable?

The terminal command: parted /dev/hdb print  will show the usage of your second ide drive.

---

### Post by defkewl on 2005-05-12
You can't mount the HD while being at that mount point

---

### Post by Nissemand on 2005-05-13
Now i just try to format it using qtparted...
I delete the old partitions, create a new one with the lable /mnt/hdd, and press Commit.
This is the screen i get:

Operation: 3 of 3.
Current operation: All operations compleated
Scanning all disk partitions.
[COLOR=Red]Error committing device.
This can happen when a device is mounted in the disk.
Try to unmount all partitions on the disk.
Please read the FAQ for this kind of error![/COLOR]

But i'm sure it's not mounted anywhere...

---

