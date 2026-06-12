---
title: "Duel boot with win7"
date: 2014-11-07
forum: General Help
---

### Post by cowboy7305 on 2014-11-07
what is the easiest way of deleting win7 from a duel boot with Ubuntu 14.04 seeing win7 is in fist partition 
or is it easier to just delete every thing and do a fresh install 
Getting rid of windows only thing i really used it for was updating my gps 
ubuntu now does most things 
Also sick of programs trying to put things on your computer via the back door with windows

---

### Post by monkeybrain20122 on 2014-11-07
Since expanding the Ubuntu boot partition to the left with gparted is tricky and takes a long time, if it is mbr I would suggest using fsarchiver to clone the Ubuntu partition, then reformat the whole drive to ext4 and then restore the Ubuntu partition. [http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

fsarchiver is in the repo. You will need an external hard drive to hold the image, and then use a live usb with fsarchiver in it (either a Ubuntu usb and install fsarchiver) or use the rescue CD as describe in fsarchiver's website to restore the image.

I can give you more info if that is the route you want to go.

BTW: duel means something like fighting to the death, I think you mean dual booting. :)

---

### Post by yancek on 2014-11-07
If you are using the Ubuntu Grub bootloader to boot, the simplet thing to do to get access to your current windows partition is to use GParted from the Ubuntu installation medium or burn it to a CD and format the windows partition to a Linux filesystem, the Ubuntu default ext4.  Create a mount point and an entry in the /etc/fstab file for it and use it for data storage.

---

### Post by Bucky Ball on 2014-11-07
As above. Open Gparted, right click and unmount the Windows partition, delete it, create an EXT partition in there (if you want) or expand the other partition into the free space, and then you may need to run Boot Repair (or open a terminal and 'sudo install-grub /dev/sda' before restarting). That should do it.

[Boot Repair.]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by nkpWyMD on 2014-11-07
Generally I recommend backing up everything important before you mess with partitions. Everyone makes mistakes.

You should be able to just install Gparted from the software center, then use the program to format the windows partition into a linux one (recommended ext4 format). Then run
```
sudo update-grub
```
so that you remove the windows entry from the grub menu.

Alternatively, if your windows partition is already residing on the same disk with a Linux partition, then you can merge the partitions together using the live CD and Gparted (running from the CD). However, if you are merging partitions you should absolutely backup everything important on an external HDD of some sort.

---

### Post by Bucky Ball on 2014-11-07
> **nkpWyMD said:**
> Generally I recommend backing up everything important before you mess with partitions.



And yes, definitely this!

---

