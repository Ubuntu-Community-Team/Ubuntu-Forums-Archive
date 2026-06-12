---
title: "extended partitions"
date: 2006-12-24
forum: General Help
---

### Post by waiotehue on 2006-12-24
When installing Ubuntu, I can create only primary partitions.  How can I create an extended partition?

Thanks for any and all help.

---

### Post by xopher on 2006-12-24
Here's some info that might help you understand partitions better:

> [SIZE="4"]_Types of partitions_[/SIZE]

**Primary**

A primary partition contains one file system. In MS-DOS and earlier versions of Microsoft Windows systems, the first partition (C:) must be a "primary partition". Other operating systems may not share this limitation; however, this can depend on other factors, such as a PC's BIOS.

Technically, a hard disk may contain as many as four primary partitions, however, typically only the active one shows up in the fdisk command.

**Extended**

An extended partition is secondary to the primary partition(s). A hard disk may contain only one. It is sub-divided into logical drives, each of which is assigned additional drive letters.

For example, a hard disk with one primary and one extended, with two logical drives, would typically show three drives, C:, D:, and E:

[http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

---

### Post by coffeecat on 2006-12-24
Are you using the live CD? Before starting the installation application, have you tried System > Administration > Gnome Partition Editor ? This starts Gparted which is the partitioner invoked by the installer, but I've never had any problems creating extended and logical partitions with it when I've started it from the menu.

---

### Post by William Pickett on 2006-12-25
CoffeeCat- help me- I am using an amd64 3200 w generic dapper_64 installed and for who knows why I have no program "gnome partition mgr" installed- I can access gparted but- here is my dilema- I want to be able to see which hdb is the current one because on this 200 g hd I have two other linuxes- had- deleted Mepis, and still have a (corrupted) dapper i686 version.

All I want to do is make sure which is /are the non-64 partitions so that I can delete the others and make room to load Winxp64 trial as comparison. Am I making sense here? ( I know I still get to educate myself, read the online manuals etc)

Thanks to all Ubuntu Community, and maybe yet we can write a better beginners book that really makes it easy to learn ( when I have more- or better use of- the time I have- hey- it would be my first book-lol) --William.

---

### Post by budgie9 on 2006-12-25
Would it not be easier to access the other partitions from your current Ubuntu install, make a note of all those partitions and then delete those partitions from Gparted.

---

### Post by bodhi.zazen on 2006-12-25
> **William Pickett said:**
> CoffeeCat- help me- I am using an amd64 3200 w generic dapper_64 installed and for who knows why I have no program "gnome partition mgr" installed- I can access gparted but- here is my dilema- I want to be able to see which hdb is the current one because on this 200 g hd I have two other linuxes- had- deleted Mepis, and still have a (corrupted) dapper i686 version.

All I want to do is make sure which is /are the non-64 partitions so that I can delete the others and make room to load Winxp64 trial as comparison. Am I making sense here? ( I know I still get to educate myself, read the online manuals etc)

Thanks to all Ubuntu Community, and maybe yet we can write a better beginners book that really makes it easy to learn ( when I have more- or better use of- the time I have- hey- it would be my first book-lol) --William.

LOL :lol:

Try these commands:

```
cat /etc/fstab
```

That will list your current partitions and will identify your current root partition.

for your other installs:
```
sudo fdisk -l
``` To list all your partitions.

You can look at /boot/grub/menu.lst to see a listing of your installs, or mount the partitions and peek at them to identify them.

I keep a text document listing my partitions like this:

partition       File system     OS
/dev/hda1    Ext3               Ubuntu
/dev/hda2    Ext3               Arch


etc ....

---

