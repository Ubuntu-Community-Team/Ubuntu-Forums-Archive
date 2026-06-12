---
title: "can't see other parts of drive"
date: 2007-03-15
forum: General Help
---

### Post by Peeda on 2007-03-15
I am brand new to Linux...When I first loaded ubuntu amd 64 I could see the other partitions on my drive.  Had some problems with the "other" operating system. Re formated the drive in 2 partitions. Loaded 1 system on one partition and the other on the other side.  NOW even the partion manager in linux says "no drives to look at"????
and I cannot see the data on the other partition (fat32)
PLEASE HELP... trying to switch to LINUX permanently.

---

### Post by taurus on 2007-03-15
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Peeda on 2007-03-15
> **taurus said:**
> Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

Like i said I'm new. 1st how do I get in the console?

---

### Post by Peeda on 2007-03-15
> **taurus said:**
> Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

Like i said I'm new. 1st how do I get in the console?

---

### Post by taurus on 2007-03-15
Click Applcations, then Accessories, then Terminal.  From that terminal, type

```
sudo fdisk -l
```
That would be lower case letter **l** as in **l**arry.  Now, paste the output of that command here.

---

### Post by Peeda on 2007-03-15
> **Peeda said:**
> Like i said I'm new. 1st how do I get in the console?

Found it! It says "command not found"

---

### Post by taurus on 2007-03-15
> **Peeda said:**
> Found it! It says "command not found"

You mean you got an error message, command not found, when you typed this one in a terminal?

```
sudo fdisk -l
```

---

### Post by Peeda on 2007-03-15
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          24        7583    60725700    c  W95 FAT32 (LBA)
/dev/hda2           14029       14593     4538362+   f  W95 Ext'd (LBA)
/dev/hda3            7584       14028    51769462+  83  Linux
/dev/hda5           14306       14593     2313328+  82  Linux swap / Solaris
/dev/hda6           14029       14305     2224939+  82  Linux swap / Solaris

Partition table entries are not in disk order

this is what I get

---

### Post by Peeda on 2007-03-15
taurus
I have to go
thanks for your help
hope you can find an answer for me 
will check back tomorow
MANY THANKS
Peeda

---

### Post by taurus on 2007-03-15
Looks like you want to mount /dev/hda1.

Edit your /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add this line to the end of it.
  
```
/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000 0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hda1
sudo mount -a
df -h  <-- you should see /dev/hda1 mounted to /media/hda1 on the list.
```

---

### Post by mrbhave on 2007-03-15
My problem might be related, but I'm not sure.  I don't understand why I lost about 23 gigs of disk space.  Running 7.04, I can tell you that I recently deleted the backups (as root) created using sbackup.  The missing disk space correlates exactly with the size of the backup folder that sbackup was using.  But as you can see from the screenshot, the missing space does not show up in the disk usage analyzer.  I should be seeing 40 gigs used, but the system isn't showing me the extra 23 (some odd) gigs that I deleted from the backup.  In GParted, I expect my /home directory to show 35.1 GB used, matching the value show in the Disk Usage Analyzer.  But GParted shows 62.43 GB, which includes the the amount of the backup folder.  As root, I have deleted the trash using  sudo rm -rf ~/.Trash but to no avail.  

Here is my screenshot:
[IMG]http://mrbhave.com/wp-includes/images/Screenshot.png[/IMG]

---

### Post by Peeda on 2007-03-16
Taurus
Many thanks.  Works like a charm
Peeda

---

