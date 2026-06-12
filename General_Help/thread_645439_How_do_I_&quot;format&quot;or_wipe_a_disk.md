---
title: "How do I &quot;format&quot;or wipe a disk?"
date: 2007-12-20
forum: General Help
---

### Post by tuproxy on 2007-12-20
I wanted to "format" or erase what I had on the drive.  I thought I could do that by deleting the partition and table. 

I did this:
sudo Fdisk /dev/sda1

I deleted the partition, added a partition and the wrote the changes on reboot.  However, All the data remains there.  Shouldn't this have erased the index?

What do I do to totally wipe a disk?  rm -rf * ?

---

### Post by mandrill on 2007-12-20
helpful to know what your final goal is - in other words, what is the mission?

---

### Post by tuproxy on 2007-12-20
The disk was used for a lot of uploading and downloading, file transfers and other temporary writing.  I just want to start over from scratch with a "clean" disk.  I don't need it zero'd out or anything.  I am just going to fill it back up with movies but wanted to start clean.  

Suggestions?

---

### Post by ~LoKe on 2007-12-20
Use gParted.

Or...assuming you did it incorrectly..

```
sudo fdisk /dev/sda1
mkfs -t ext3 /dev/sda1
```

---

### Post by niteshifter on 2007-12-20
You've these options:

Via command line;
```
cd /mount-point/folder-name
ls
rm -rf * 
```
Replace mount-point and folder-name to fit your installation. The ls is a safety / sanity check, let's you see what the rm command is going to blow away. It's a good habit to make.

Or
```
mkfs -t ext3 /dev/Tdxy
```
Where T is h or s (IDE or SATA), x is a,b,c etc. (the drive) and y is 1, 2, 3 etc (the partition number). This makes a new filesystem. Risky business this is: Make ABSOLUTELY SURE you have the correct device!

Or
With the GUI (Nautilus in GNOME): navigate to the desired folder, press Ctlr+H (to show hidden files), then Ctrl+A (to select all) then Shift+Del (to delete absolute). 
For KDE, maybe a KDE user will chime in here.

The GUI way is "better":  no worries about typos in device names or folder names, you see what you're deleting. 

As to why deleting the partition then creating it didn't erase the files: All a partition editor does is edit the partition table (a small chunk of data at the physical start of the disc), not the data on the partition itself.

---

### Post by chris4585 on 2007-12-20
When i want to delete partitions i use gparted CD, it gets the job done

---

### Post by mandrill on 2007-12-20
I agree g-parted disc will do it. Or, Ultimate boot disc, but that has options for wiping as well....

---

