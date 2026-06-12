---
title: "[SOLVED] Ubuntu won't recognize my FAT32 partition"
date: 2008-02-01
forum: General Help
---

### Post by Warren Watts on 2008-02-01
I have a 120GB SATA drive I was previously using in a windows box, and I had the drive split into three 40GB partitions.  One partition is formatted NTFS, the other two FAT32.

I purchased a PCI SATA card, connected the drive, rebooted the computer, and Ubuntu 7.04 recognized the hardware no problem.  

The problem is, Ubuntu only "sees" the NTFS partition.  I booted the computer with a live GParted CD, and GParted recognizes all three partitions.  One of the partitions was empty, so I reformatted it as NTFS and rebooted into Ubuntu, and now Ubuntu sees the two NTFS partitions, but still acts like the FAT32 partition isn't even there.

What do I need to do to make Ubuntu see the FAT32 partition?  I have about 35GB of files on the partition, and I want to see what is there before I wipe the partition.

I suppose I could pull the card and the drive out and stick them in a windows box and load the stupid RAID drivers for the SATA card,  but that seems like a lot of trouble just to see what's on the partition.  

It was so easy with Ubuntu.  I just installed the card, rebooted and boom, there it was.

Any suggestions?

---

### Post by fjgaude on 2008-02-01
You have to mount the partitions using the mount command. You can have them mounted automatically if you place them in your /etc/fstab file. Can you do these things?

---

### Post by polmir on 2008-02-01
```
sudo apt-get install ntfs-3g
```
restart Ubutu
and type in terminal
```
gedit /etc/fstab
```
```
sudo fdisk -l /dev/sda
sudo fdisk -l /dev/sdb
```
sda or hda... 

please post output info

---

### Post by Warren Watts on 2008-02-02
Well, between the suggestions provided by fjgaude and the suggestions provided by polmir, I was able to locate and auto mount using fstab all three partitions on the SATA drive.

Thanks, guys!

---

### Post by fjgaude on 2008-02-02
Very good, so nice to achieve success, eh?

We learn as we do.

---

