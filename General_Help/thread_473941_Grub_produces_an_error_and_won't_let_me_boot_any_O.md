---
title: "Grub produces an error and won't let me boot any OS"
date: 2007-06-14
forum: General Help
---

### Post by zangelacos on 2007-06-14
I recently made a partition change within Windows, and now Grub won't load correctly. Consequently, I can't use the computer.

When I boot up, it says that it's loading GRUB, then I get "Error 17" and a blank flashing line. Anyone know if there's something I can do about this? Thanks

---

### Post by meman63 on 2007-06-14
Can you boot into recovery console?

Just in case,to do that,press ESC right after the bios screen goes off.

Cheers,
    Meman63

---

### Post by floke on 2007-06-14
From live cd - in a terminal - post the output of

sudo fdisk -l

This will list your partitions - you need to find the one with ubuntu on it. 
Then mount the partition - lets say it's sda1
First, make a place to mount it

mkdir /home/ubuntu/here

Then mount it

sudo mount /dev/sda1 /home/ubuntu/here

Then check the grub file

sudo cat /home/ubuntu/here/boot/grub/menu.lst

post the output of this - I bet its now pointing to the wrong partition and we need to change it.

---

### Post by zangelacos on 2007-06-14
> **Steve.K said:**
> From live cd - in a terminal - post the output of

sudo fdisk -l

This will list your partitions - you need to find the one with ubuntu on it. 
Then mount the partition - lets say it's sda1
First, make a place to mount it

mkdir /home/ubuntu/here

Then mount it

sudo mount /dev/sda1 /home/ubuntu/here

Then check the grub file

sudo cat /home/ubuntu/here/boot/grub/menu.lst

post the output of this - I bet its now pointing to the wrong partition and we need to change it.
Well... here's what I'm getting
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2        6532    52460254+   7  HPFS/NTFS
/dev/hda2            6533        6634      819315   82  Linux swap / Solaris
/dev/hda3            8261        9729    11799742+   7  HPFS/NTFS
/dev/hda4            6635        8260    13060845    5  Extended
/dev/hda5            6635        8260    13060813+   7  HPFS/NTFS

Partition table entries are not in disk order
ubuntu@ubuntu:~$ mkdir /home/ubuntu/here
mkdir: cannot create directory `/home/ubuntu/here': File exists
ubuntu@ubuntu:~$ sudo mount /dev/hda4 /home/ubuntu/here
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo cat /home/ubuntu/here/boot/grub/menu.lst
cat: /home/ubuntu/here/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 

```

Does that help?

---

### Post by floke on 2007-06-14
Yep. It looks like you've deleted your ubuntu, so I guess that's why it won't load!

---

### Post by zangelacos on 2007-06-14
Yeah that's what I meant to do, but I didn't think that it would kill Grub too. :( Is there any way that I can set it to load my Windows partition by default?

Or better yet, any way to just get it booting up again?

---

### Post by floke on 2007-06-14
Grub sits on your mbr and when you boot up it points to the partition with the menu.lst file on - which is no longer there.
To fix it you will have to reinstall windows - or put the rescue disk in and use 'fixmbr' - do a search around here for instructions on how to do this.

---

