---
title: "Mounting sda2"
date: 2007-09-22
forum: General Help
---

### Post by Zigbigadoorlue on 2007-09-22
I have several hard drives and many partitions on my computer that I am trying to convert from windows to Ubuntu and consequently from NTFS to ext3. My plan is to create a large enough ext3 partition that i can transfer all the data from each of my partitions, format that partition to ext3, and than transfer the data back.  

On my largest drive I resized the NTFS partition that encompassed the whole drive with Partition Magic so that it only took up half the drive. I than used GParted to format the freed space into a ext3 partition. But I could not find the partition because it hadn't been mounted (why doesn't Ubuntu do this automatically?). I then issued this command to mount the second SATA partition to my media directory: 'sudo mount -t  ext3 /dev/sda2 /media' . For some reason this got rid of (unmounted?) everything in /media and replaced it with a file called "lost+found" that I cant access either through the GUI or terminal. When I try to open any of my HDD partitions through the GUI I get "could not open location 'file:///media/hdb1' The location or file could not be found". I can put in and play an audio cd which is perplexing.

Am I mounting wrong? I just want to mount this partition so I can find its UUID and add it, and the other ext3 partitions I'm going to make, to fstab. Any help is appreciated.

~Rowan

---

### Post by dcstar on 2007-09-22
> **Zigbigadoorlue said:**
> I have several hard drives and many partitions on my computer that I am trying to convert from windows to Ubuntu and consequently from NTFS to ext3. My plan is to create a large enough ext3 partition that i can transfer all the data from each of my partitions, format that partition to ext3, and than transfer the data back.  

On my largest drive I resized the NTFS partition that encompassed the whole drive with Partition Magic so that it only took up half the drive. I than used GParted to format the freed space into a ext3 partition. But I could not find the partition because it hadn't been mounted (why doesn't Ubuntu do this automatically?). I then issued this command to mount the second SATA partition to my media directory: 'sudo mount -t  ext3 /dev/sda2 /media' . For some reason this got rid of (unmounted?) everything in /media and replaced it with a file called "lost+found" that I cant access either through the GUI or terminal. When I try to open any of my HDD partitions through the GUI I get "could not open location 'file:///media/hdb1' The location or file could not be found". I can put in and play an audio cd which is perplexing.

Am I mounting wrong? I just want to mount this partition so I can find its UUID and add it, and the other ext3 partitions I'm going to make, to fstab. Any help is appreciated.

~Rowan

```
sudo umount /media
sudo mkdir /media/sda2
sudo mount -t  ext3 /dev/sda2 /media/sda2
```

Then edit your /etc/fstab file and add in the relevant line to mount that filesystem on startup.

---

### Post by glotz on 2007-09-22
Yes, you're mounting wrong! :D

First you make a folder as a mount point
e.g. mkdir /mnt/name

Then you mount your disk using the new folder as mount point.

(you can use mnt or media just as you please, usually the harddisks are mounted into mnt and removable media into media)

Welcome to Ubuntu mate!

---

