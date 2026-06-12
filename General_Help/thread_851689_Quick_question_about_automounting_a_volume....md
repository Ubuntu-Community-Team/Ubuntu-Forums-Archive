---
title: "Quick question about automounting a volume..."
date: 2008-07-06
forum: General Help
---

### Post by munkyinvasion on 2008-07-06
I have my hard drive in 5 partitions right now, and one is for media. So, my question is, how do i auto-mount that media volume when i boot, because all my music players freak out when it isn't mounted.

Thanks

---

### Post by scragar on 2008-07-06
I don't suppose you happen to know it's partition number?

try mounting it first how you are doing it currently, then post the output of ```
mount
``` or atleast the line to do with your media folder(if you can't find it don't worry :P)

---

### Post by munkyinvasion on 2008-07-06
lets see. Toshiba is partition 1, vista is 2 so thats makes the Media one 3. Ubuntu is 4 and 5. And I usually just click it in Places, but it is "in" /media/Media.

Or are you looking for /dev/sda3?

---

### Post by iaculallad on 2008-07-06
> **munkyinvasion said:**
> I have my hard drive in 5 partitions right now, and one is for media. So, my question is, how do i auto-mount that media volume when i boot, because all my music players freak out when it isn't mounted.

Thanks

You can automount that volume using your fstab file. On your terminal, issue the commands below and post whatever it displays so we could help you with the steps:

```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by munkyinvasion on 2008-07-06
Should i run those with or without it mounted?

---

### Post by scragar on 2008-07-06
sda3, so first create a folder for it:
```
sudo mkdir /media/media
```
then edit the fstab:
```
gksudo gedit /etc/fstab
```
and copy/paste this line in at the end:
```
/dev/sda3 /media/media     auto    defaults        0       2
```
close the text editor and next time you restart it should automount to /media/media(change the path as you want/need to)

---

### Post by iaculallad on 2008-07-06
> **munkyinvasion said:**
> Should i run those with or without it mounted?

With or Without it mounted can do.

---

### Post by munkyinvasion on 2008-07-06
The output of those 2 commands is

josh@josh-ubuntulappy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=a31ce2c0-3621-45d6-8384-a5a4cb696c3d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=52a8a141-ff73-44fe-aa35-66131cc52e2b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 /media/media     auto    defaults        0       2
josh@josh-ubuntulappy:~$ sudo fdisk -l
[sudo] password for josh: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3eab369d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192       14039   111229128    7  HPFS/NTFS
/dev/sda3           14039       21535    60212224    7  HPFS/NTFS
/dev/sda4           21536       24321    22378545    5  Extended
/dev/sda5           21536       24200    21406581   83  Linux
/dev/sda6           24201       24321      971901   82  Linux swap / Solaris

and i want the 3rd one

---

### Post by iaculallad on 2008-07-06
First step is to install ntfs-3g utility:

```
sudo apt-get install ntfs-3g
```

Secondly, create a mount point for the SDA3 partition: we name it as mymedia.

```
sudo mkdir /media/mymedia
```

And lastly, we open your /etc/fstab file for editing:

```
gksudo /etc/fstab
```

and insert the line of text below at the last-part of your fstab file:

```
/dev/sda3 /media/mymedia ntfs-3g auto defaults 0 0
```

For ending:

```
sudo mount -a
```

---

### Post by scragar on 2008-07-06
> **iaculallad said:**
> 
and insert the line of text below at the last-part of your fstab file:

```
/dev/sda3 /media/mymedia ntfs-3g auto defaults 0 0
```


**[size=5]DON'T INSERT THAT LINE!![/size]**

it's got too many arguments :P, either remove the auto or remove the ntfs-3g, otherwise you'll get a few complaints during boot.

---

### Post by munkyinvasion on 2008-07-06
OH NOES!!!! Remove which?

---

### Post by scragar on 2008-07-06
doesn't matter, personaly I would leave it as auto, since that will automaticly detect the file system type, so there are no worries about having deleted/reformated the partition at a later date. On the other hand it is a faction slower since it has to read in the format from a different part of the HD as it is reading to load the rest of the info(although it's barely noticable).

Choice is yours.



Oh, if your adding the line he stated remove the line I told you to add, otherwise they'll both try to mount the partition and you'll get an error message(it'll still boot though)

---

### Post by iaculallad on 2008-07-06
> **munkyinvasion said:**
> OH NOES!!!! Remove which?

My typo-error:

That should be:

> /dev/sda3 /media/mymedia ntfs-3g defaults 0 0

---

### Post by munkyinvasion on 2008-07-06
It works! Thanks a bunch and a half!

---

