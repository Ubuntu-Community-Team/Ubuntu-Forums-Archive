---
title: "formatting hard drive partition"
date: 2007-12-12
forum: General Help
---

### Post by lowebb on 2007-12-12
An easy question. I've a partitioned HD with a vfat partition which has no info on it which I need (it is not '/', it is mounted seperately to '/vfat')

I've recently got myself Hi-Def capability and realised I was going to have issues with the max file size of 4GB. I need to be able to format this drive without fecking up my ubuntu install. Firstly should I simply format it to ext3 and secondly how do I do this easily, there must be a nice command

Thanks

---

### Post by Keith Hedger on 2007-12-12
From the terminal:
sudo umount /dev/WHATEVER
sudo mkfs.ext3 /dev/WHATEVER

/dev/WHATEVER=your vfat disk
Or you can use gparted which is the gnome graphical partition editor, either way be VERY careful about what you partition as theres no going back!

---

### Post by lowebb on 2007-12-12
So I need to work out what the name of my partition is in the /dev/WHATEVER directory. Yeah? Ok thats seems easy. Would this be defined in the fstab? I assume this will auto-remove all data on this partition

---

### Post by Keith Hedger on 2007-12-12
To reiterate, yes formating a drive will completly wipe ALL data from that drive.
To find the dev use "mount" to list all mounted drives or "sudo fdisk -l" to list all partions, if you are letting gmome mount your drive then no you should not have to alter fstab however if you have manually added it to fstab or the system added it to fstab when u installed ubuntu, u may have to alter fstab as the uuid of the drive will change when u format it

---

