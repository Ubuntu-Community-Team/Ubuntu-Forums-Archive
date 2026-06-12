---
title: "Mount FAT32 partition"
date: 2004-11-13
forum: General Help
---

### Post by Ozitraveller on 2004-11-13
How do I mount the FAT32 (windows) partition I created during the installation? I can see it in Nautilus, but I can't do anything with it.

Thanks

---

### Post by adbak on 2004-11-13
I have a FAT32 partition mounted on my system and this is what I have in my /etc/fstab:
```

/dev/hda2       /swap           vfat    defaults        0       2

```

hda2 is the partition that it's on.
/swap is where I have it mounted.
vfat, I guess, is what Linux calls FAT32.
I have no idea what the rest means.

Just add this to your /etc/fstab if you want to have it mounted each time you boot up.

---

### Post by conchobar on 2004-11-13
First, you'll need to post the contents of your fstab file. If you aren't familiar with that, type this into either "Run Application..." or a terminal:
gedit /etc/fstab

---

### Post by Ozitraveller on 2004-11-13
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /home           ext3    defaults        0       2
/dev/hdb5       /windows        vfat    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


If this means it's mounted, then how do I create folders within it?

---

### Post by conchobar on 2004-11-13
You have the Vfat partition's options set to defaults, which is probably the problem: one of the defaults is "nouser" meaning that only root can mount the drive. Since Ubuntu has no root account, that doesn't let you do a whole lot. :)

Try replacing "defaults" with this string:
users,umask=0,auto

"users" so that every account can access it, "umask=0" so that every account has permission to read, write, and execute from it (if you want to restrict access to it, Google "umask fstab" to see what numbers grant what abilities), and "auto" so that it's mounted automatically when you boot.

---

### Post by candymanobh3 on 2004-11-13
[QUOTE=Ozitraveller]
/dev/hdb5       /windows        vfat    defaults        0       0
[/QUOTE]

Make sure /windows exists. If not, create it. I'm not used to mounting drives directly under /. I have not been able to boot into Ubuntu, but usually it would be /mnt/windows. To each his own, I guess.

---

### Post by Ozitraveller on 2004-11-14
Thanks conchobar. I should have been a little more careful when I did the install.

---

### Post by Marauder1 on 2004-11-14
But Conchobar ...

Is it better to put the option vfat or auto when
mounting a fat32 partition ?

---

### Post by conchobar on 2004-11-14
Marauder: I can't think of any reason to use "auto" when you know for sure that it's a vfat partition. "auto" would come in handy for things like floppies and cd-roms where you might not be sure of the filesystem type.

Also, to clarify, fat32 is the same thing as vfat as far as Linux is concerned.

---

### Post by anklator on 2004-11-14
here u have my fstab

type

nano -w /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda9       /               reiserfs noatime         0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda6       /mnt/hda6       vfat    user,uid=1000   0 0
/dev/hda7       /mnt/hda7       vfat    user,uid=1000   0 0
/dev/hda1       /mnt/hda1       ntfs    user,uid=1000   0 0

remenber fat32 is called vfat on linux

---

### Post by Marauder1 on 2004-11-14
Thanks conchobar, i made the switch  \\:D/

---

### Post by Dylanby on 2004-11-28
For a vfat (fat32) partition under 'options', what is the difference between these two?

=> defaults,uid=1000,gid=1000        0       0

&

=> defaults,umask=000        0       0

Is one more "correct" or secure/insecure? I'm a newbie so any responses should be "newbified". Thanks.

---

