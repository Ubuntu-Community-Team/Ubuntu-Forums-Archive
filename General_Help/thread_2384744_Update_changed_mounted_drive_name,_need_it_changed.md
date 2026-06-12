---
title: "Update changed mounted drive name, need it changed back"
date: 2018-02-11
forum: General Help
---

### Post by forleafe on 2018-02-11
Recently my mounted Hard disk drive in media/bryan/46AA1E1FAA1E0C55 changed and added a 1 at the end. Very annoying, as now my symlinks are broken and a few programs I run all don't work. All I want is to change the name back to what it was. How do I do this easy and painlessly?

Please note, I've spent about 2 hours trying to figure this out, and have found a lot of information, but none of it really pertaining to my specific situation. I'm sure this has happened before, but I'd really like help on my specific situation. Also, I'm on Ubuntu 16.04 if that helps at all.

---

### Post by #&amp;thj^% on 2018-02-11
> **forleafe said:**
> Recently my mounted Hard disk drive in media/bryan/46AA1E1FAA1E0C55 changed and added a 1 at the end. Very annoying, as now my symlinks are broken and a few programs I run all don't work. All I want is to change the name back to what it was. How do I do this easy and painlessly?

Please note, I've spent about 2 hours trying to figure this out, and have found a lot of information, but none of it really pertaining to my specific situation. I'm sure this has happened before, but I'd really like help on my specific situation. Also, I'm on Ubuntu 16.04 if that helps at all.
**_EDIT: Before making changes like this on a system>>>BE SURE to have your Back-ups in place._** (You've been warned)
I have seen this behavior also. ;)
To change the labels of drives use one of these commands:
```

sudo e2label /dev/sdc6 Data
```

OR

```

sudo sudo tune2fs -L Data /dev/sdc6
```

**Replace** "**/dev/sdc6**" with the specific drive you want to label and **"Data"** with the desired label or UUID.

Use **sudo fdisk -l **to find drive names.
```
sudo fdisk -l 
```

You can use Gparted to do this also:
In gparted right click the disk or partition and look for "Lable file system" or UUID >>(2 sperate choices)

---

### Post by coffeecat on 2018-02-11
Excellent advice from 1fallen to label the partition so that your mountpoint gets a more human-readable name. However, this **will** break all your symlinks, and you will need to redo them all. 

When a device is unexpectedly automounted to a mountpoint that has a 1 added to the previous mountpoint name, this is because the old mountpoint wasn't deleted when it should have been. When you came to remount the partition named 46AA1E1FAA1E0C55, the system found an empty directory named media/bryan/46AA1E1FAA1E0C55 and created a new one named media/bryan/46AA1E1FAA1E0C55-1 or media/bryan/46AA1E1FAA1E0C551 or however the 1 was appended (as a failsafe), and then mounted the partition on the new mountpoint.

All you need do is to delete the old mountpoint and then it will be re-created with the name you expect next time the partition is mounted.

Unmount the partition (for safety) and run this terminal command:

```
sudo rmdir media/bryan/46AA1E1FAA1E0C55*
```

Don't forget the asterisk at the end. That will deal with any other iterations and will remove any directories with a name that includes the string 46AA1E1FAA1E0C55 in /media/bryan.

Having said all that, if you have symlinks and other stuff expecting a fixed mountpoint, it is better to use a custom line in /etc/fstab, but that's another ball-game. Using the automounting function built into the GUI is fine most of the time, but you need to be aware that just occasionally the mountpoint will change and you need to know how to deal with this.  

Co-incidentally the same thing happened to me today. :)

---

### Post by forleafe on 2018-02-11
> **coffeecat said:**
> Excellent advice from 1fallen to label the partition so that your mountpoint gets a more human-readable name. However, this **will** break all your symlinks, and you will need to redo them all. 

When a device is unexpectedly automounted to a mountpoint that has a 1 added to the previous mountpoint name, this is because the old mountpoint wasn't deleted when it should have been. When you came to remount the partition named 46AA1E1FAA1E0C55, the system found an empty directory named media/bryan/46AA1E1FAA1E0C55 and created a new one named media/bryan/46AA1E1FAA1E0C55-1 or media/bryan/46AA1E1FAA1E0C551 or however the 1 was appended (as a failsafe), and then mounted the partition on the new mountpoint.

All you need do is to delete the old mountpoint and then it will be re-created with the name you expect next time the partition is mounted.

Unmount the partition (for safety) and run this terminal command:

```
sudo rmdir media/bryan/46AA1E1FAA1E0C55*
```

Don't forget the asterisk at the end. That will deal with any other iterations and will remove any directories with a name that includes the string 46AA1E1FAA1E0C55 in /media/bryan.

Having said all that, if you have symlinks and other stuff expecting a fixed mountpoint, it is better to use a custom line in /etc/fstab, but that's another ball-game. Using the automounting function built into the GUI is fine most of the time, but you need to be aware that just occasionally the mountpoint will change and you need to know how to deal with this. 

Co-incidentally the same thing happened to me today. :)

tried your command and I got:

rmdir: failed to remove 'media/bryan/46AA1E1FAA1E0C55': Directory not empty


...Which is total crap because it is empty :c

---

### Post by #&amp;thj^% on 2018-02-11
If this is a mount point,** it should be unmounted before deleting.** If it is a normal directory, sometime there might be some open handles causing  the problem. Reboot your machine once and try to delete it.
BTW Thanks coffeecat, Your wording is a lot better than mine. :)

---

### Post by forleafe on 2018-02-13
[img]https://i.imgur.com/ZBTLZ3N.jpg[/img]
[https://imgur.com/ZBTLZ3N](https://imgur.com/ZBTLZ3N)

So I tried a fresh restart, making sure the drive was unmounted, I ran the command again and got the error message shown in the description. The crazy stupid thing is the file that it says doesn't exist is sitting right in the file directory as an empty folder, impervious to deletion apparently. Every time I remount my drive, it comes back with an extra 1 added to its name. This empty ghost folder appears to be the root of the problem.

On a side note, I adore linux, but sweet baby jesus sometimes the most basic of basic things with it can be an utter nightmare.

---

### Post by forleafe on 2018-02-13
Okay fixed it. The code below removed the empty directory in media/bryan/ 

sudo rm -r /media/bryan/46AA1E1FAA1E0C55*

When I remounted my drive it was named properly. Yayyyyyyy

---

