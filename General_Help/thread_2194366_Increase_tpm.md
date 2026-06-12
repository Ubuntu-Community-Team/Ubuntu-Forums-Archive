---
title: "Increase /tpm"
date: 2013-12-18
forum: General Help
---

### Post by borgward on 2013-12-18
How do I increase the size of /tmp? I need a minimum of 8.4GB. I have 8.3 GB fr
ee space.

Partition 1 is 15 GB.

Extended Partition 2 is 735 GB it is divided:

Swap partition 5 4.0 GB swap 
Filesystem partition 6 731 GB ext 4

---

### Post by 3rdalbum on 2013-12-18
Well, you could free up a little bit of space on your regular filesystem. Surely on a 731 gigabyte filesystem you can find a hundred megs to remove? You could copy a large file to another disk and then remove it from your 731gb partition to free up this space.

If this is really impossible for you, there's another way.

If you have a 16 gb flash drive or bigger (or a hard disk) you can mount it as /tmp. To do this:

First, format it to ext3 or ext4. You will lose all data on the disk when you format it, and every time you shut down you will lose all data in /tmp.

Second, open the file /etc/fstab as root and add a new line for this disk. The mount point should be /tmp, type is either 'ext3' or 'ext4', options can be 'defaults', dump and pass should both be '0' (zero). The file system should be the device file or UUID of the disk - to find this out, open another terminal and run:

```
sudo fdisk -l
```

The device file should look something like: /dev/sdb or /dev/sdc1 or something like that.

Save your changes to the /etc/fstab file and reboot with the drive in. Do whatever you need to do that requires more /tmp space, and then when you're finished reverse the changes to your /etc/fstab file. DO NOT FORGET TO REVERSE THE CHANGES AS SOON AS YOU ARE DONE, OR YOU WILL LIKELY LOSE DATA ON ANY DISK YOU PLUG IN AT BOOT.

---

### Post by rnerwein2 on 2013-12-18
hi
my only answer is: 3 * 9 = google
ciao

---

### Post by grahammechanical on 2013-12-18
It is possible to install Ubuntu using the Something Else option and set /tmp on a separate partition.

---

