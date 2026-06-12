---
title: "how do i mount a drive?"
date: 2007-04-25
forum: General Help
---

### Post by creamcheeze77 on 2007-04-25
i recently tried to upgrade to 7.04 from edgy, which failed miserably ( the exact problem is at [http://ubuntuforums.org/showthread.php?p=2528766#post2528766](http://ubuntuforums.org/showthread.php?p=2528766#post2528766) ).  the only option i can see is to just do a clean install of Edgy.  all of my data, which i don't want to lose, was on a 500gb sata drive.  i don't want to lose my stuff, so since i have four of the drives, three of which were unused, i was going to install edgy on a blank drive, then plug in the drive that had feisty installed and copy all of my stuff to the new one.  is this possible, and if so, how? thanks in advance.

---

### Post by strabes on 2007-04-25
Why don't you just install feisty on the drive inside the computer (using the alternate install CD) and then just use one of the externals as data storage?

---

### Post by creamcheeze77 on 2007-04-25
the problem is that feisty won't install at all, it wont even load from a CD, even with nothing except the motherboard, ram, and a blank hard drive.  i just want to retrieve some files from the hard drive that has feisty on it, so my question was just how do you mount drives in ubuntu?

---

### Post by rsay on 2007-04-26
There are several ways to get a drive mounted.

If its in the computer somewhere you just mount it by referencing the device:

If you don't know which device it is, use ```
fdisk -l 
```to see what drives are available.

Then, decide on a mountpoint in your file system
```
mkdir /mnt/mydisk
mount -t auto /dev/hda2 /mnt/mydisk
```

you can use:```
 man mount
```  for more info.

If the drive isn't in the computer you can stick it in an external usb drive enclosure and just plug it in to a usb port and wait for it to automount and copy your files.

This also brings up a point about disk partitioning. I like to keep my data files independent of my operating system so I store my documents in a data partition on the drive separate from the OS. That way I can re-install any time on the operating system partition without copying or jeopardizing my data. In fact, I keep two operating system partitions so that when a new version comes out I can install on the OS partition that I'm not using and play with the new distro. When or if I decide that the new distro is ready to be the primary I just change grub to boot the new OS as the default. I am then free to delete the old distro until I find something new to play with.

---

### Post by creamcheeze77 on 2007-04-30
i did this and i think it erased my hard drives...
now when i boot up the computer it says "failed to find operating system"

---

