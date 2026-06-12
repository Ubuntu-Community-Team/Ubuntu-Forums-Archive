---
title: "Missing some Menu options"
date: 2007-01-15
forum: General Help
---

### Post by Happy_Man on 2007-01-15
Hey everyone.

I did a standard install of edgy from the livecd and let the installer do my partitioning. Now i cant find my windows partition anywhere. Some posts on this forum said to go to system-admin-disk to fix it. I don't have a disk option. :-k This is really bugging me, because I hate having to switch OS's every time I want to transfer something. Also, could someone give me a complete list of all the system menu options? I think I'm missing other stuff there too. Thanks!

---

### Post by peabody on 2007-01-15
Do you have the Alacarte menu editor in your menu?  You should be able to use that to turn on menu options that have been disabled.

---

### Post by Happy_Man on 2007-01-15
No...

---

### Post by Happy_Man on 2007-01-15
He he. Whoops, I do have Alacarte, but there's no "disk" option.

---

### Post by peabody on 2007-01-15
I'm still on dapper so I don't know if anything's changed, but the disks control panel should be under the Administration menu.

---

### Post by Happy_Man on 2007-01-15
Everything's checked under administration....grrrrr!](*,)

---

### Post by peabody on 2007-01-15
Sorry, looks like you'll have to ask someone running Edgy.  The control panel may have changed name.

---

### Post by hikaricore on 2007-01-15
I believe the disks cp was scrapped from edgy due to it being outdated and not working correctly as the original developer ceased work on the project.  There will be I think a replacement in fiesty, and I know there's a decent gnome application out there that works just as well.  Someone sent me a link to it once but I can't find it at the moment.  I'll check my admin menu when I get home as I know I added this new application there.

---

### Post by bapoumba on 2007-01-15
hi,
In the meantime, what is the output to **cat /etc/fstab** ?

There is also an option in gconf-editor (> apps > nautilus > desktop  --> tick volumes_visible) that will show on the desktop anything mounted in /media (by default, if declared during the install process, detected Windows partitions are mounted in /media).

---

### Post by Happy_Man on 2007-01-15
> **bapoumba said:**
> hi,
In the meantime, what is the output to **cat /etc/fstab** ?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=b7c0b192-06fd-4836-9e32-0105fce7c026 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=44afe890-6d31-4bdf-ad18-0ecff36efb94 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

That...

---

### Post by bapoumba on 2007-01-15
Okay, that's what I understood from your first post :

> **Happy_Man said:**
> ...
I did a standard install of edgy from the livecd and let the installer do my partitioning. Now i cant find my windows partition anywhere...

I'm afraid you let the installer use the _whole_ disk to install Ubuntu. Do you have several hard drives ?

---

### Post by Happy_Man on 2007-01-15
> **bapoumba said:**
> 
I'm afraid you let the installer use the _whole_ disk to install Ubuntu. Do you have several hard drives ?

I definitely didn't. Let me rephrase: I can't find my windows partition from *Ubuntu*. I can still *boot* Windows just fine.

---

### Post by bapoumba on 2007-01-15
One more thing, if you have other hard drives, what's the output to** sudo fdisk -l** ?

---

### Post by Happy_Man on 2007-01-15
> **bapoumba said:**
> One more thing, if you have other hard drives, what's the output to** sudo fdisk -l** ?

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           5       40131   de  Dell Utility
/dev/hda2   *           6        9158    73521472+   7  HPFS/NTFS
/dev/hda3            9159       14500    42909615   83  Linux
/dev/hda4           14501       14593      747022+   5  Extended
/dev/hda5           14501       14593      746991   82  Linux swap / Solaris

As I said, my Windows is still there. What now?

---

### Post by lalmeras on 2007-01-15
in the /etc/fstab, you can see that Ubuntu is installed on the /dev/hda3 device (the / mount point).

Your windows partition is surely on the /dev/hda1 device (first partition of the disk).

So

sudo mkdir /media/hda1
sudo mkdir /media/hda2
sudo mount /dev/hda1 /media/hda1
sudo mount /dev/hda2 /media/hda2

You can now browse /media/ folder to see if your data are here.
If this is the case, you have to add a line in the /etc/fstab file for the right partition (/dev/hda1 or /dev/hda2).

---

### Post by lalmeras on 2007-01-15
With the last information, it's /dev/hda2 the right partition.

---

### Post by Happy_Man on 2007-01-15
Sweet! That solved my drive access problem. Only one thing-why do you have to have root privileges to access the windows partition?

---

### Post by peabody on 2007-01-15
> **Happy_Man said:**
> Sweet! That solved my drive access problem. Only one thing-why do you have to have root privileges to access the windows partition?

Depends, if the partition is ntfs, there isn't native write support for ntfs built into the kernel.  For that you want to look into an app called ntfs-3g.  I believe there's a howto on the forum that describes how to get it working.

If it's fat32, there should be a parameter for the /etc/fstab line to change the default permissions of the mount.

---

### Post by lalmeras on 2007-01-15
It is the default mount option. Read this to add a permanent mount with the right options [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

