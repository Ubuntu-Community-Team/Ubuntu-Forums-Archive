---
title: "Problems mounting Windows partitions"
date: 2007-07-31
forum: General Help
---

### Post by bsmith on 2007-07-31
Hi, I need help with mounting my windows partitions, they mount ok, and I can access them as super user, but if I try to look in the folder as my normal login I get the error...

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "vista".

What have I done wrong?

Below is my fstab file, with the bottom 2 lines that I have added, also what are the UUID lines in there, I have not seen them in the fstab tutorials I have written.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=80595967-d3ab-4a03-9b39-3af56adefe32 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=7573e157-df82-44a0-b343-2d597ae09bb0 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


/dev/sda1	/mnt/vista	auto	rw,noauto,user	0	0
/dev/sda2	/mnt/xp		auto	rw,noauto,user	0	0

```

Thanks in advance

---

### Post by sdowney717 on 2007-07-31
this is likely not an fstab problem. here is mine
I can access win xp home files from root login and normal login. So perhaps something to do with permissions. for me it shows up as disk or 116.9gb volume  in places/computer

I am not running ntfs-3g, and ntfs-3g has a config program to automatically setup read write to ntfs partitions.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d6269386-1a91-432d-9014-cce8e93eb891 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f0c3f9d6-39e2-4bf4-8d9c-03e28e2b8ad3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by merlinus on 2007-07-31
First off, no filesystem type is specified, e.g. ntfs.  That may be part of your problem.

-merlin

---

### Post by bsmith on 2007-07-31
Thanks for the quick replys, if I run nautilus as superuser I can list all the files, and read them on both mounts, and when i try to change the permissions on either folder, it says the the drive is read-only, but I clearly put in rw in the fstab

Any Ideas.

---

### Post by merlinus on 2007-07-31
Once again, what is the filesystem?

If ntfs, try installing ntfs-3g and ntfs-config.

-merlin

---

### Post by bsmith on 2007-07-31
Sorry, I forgot to mention they are both NTFS
I have just installed ntfs-3g, but I could not find ntfs-config in synaptic package manager.
do I need to change my fstab

Thanks

---

### Post by merlinus on 2007-07-31
```

sudo apt-get ntfs-3g ntfs-config

```then

```

sudo ntfs-config

```Tick the appropriate boxes and restart.

Then post:

```

cat /etc/fstab

```-merlin

---

### Post by bsmith on 2007-07-31
```
ben@matrix:~$ sudo apt-get ntfs-3g ntfs-config
E: Invalid operation ntfs-3g
ben@matrix:~$ sudo apt-get install ntfs-3g ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
E: Couldn't find package ntfs-config
```

Is there a repository i need to add

---

### Post by merlinus on 2007-07-31
Is there an NTFS Configuration Tool listed in Applications/System Tools?

-merlin

---

### Post by bsmith on 2007-07-31
Not that I can see

---

### Post by merlinus on 2007-07-31
Have you restarted since installing ntfs-3g?  If not, try it and see if the tool shows up.

Otherwise, give this a shot:

```

sudo apt-get update
sudo apt-get install ntfs-config

```

-merlin

---

### Post by bsmith on 2007-07-31
Hey, all fixed, thanks to your help.
I found ntfs-config on [www.gnomefiles.org](www.gnomefiles.org), and after running it, everything works perfectly.

Thanks again.

---

