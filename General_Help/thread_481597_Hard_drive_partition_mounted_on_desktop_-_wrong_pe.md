---
title: "Hard drive partition mounted on desktop - wrong permissions"
date: 2007-06-22
forum: General Help
---

### Post by tedrogers on 2007-06-22
Hi there all ubuntuians,

WIthin Feisty, I have a partition mounted on my desktop that I can't unmount because it is not allowed and also I do not own as a regular user (root owns it).

I also do not have write access to it, i.e. I cannot copy anything to it.

How can I change permissions of this drive so that I own it?

I have tried this (name:name is obviously replaced by my username) but it does nothing:

```
sudo chown -R name:name /dev/hda5
sudo chmod 775 -R /dev/hda5
```

Basically, I would like a few things...

1. No hard disk partition on the desktop, instead being in the /mnt directory
2. Permissions to read/write from the partition

I have a limited understanding of /etc/fstab so I'm pretty much stuck now.

Any ideas?

Thanks in advance.

[may the ubuntu grow strong within you - nice to see Dell on board - lets have more of this!]

---

### Post by benerivo on 2007-06-22
The answer would be in changing your /etc/fstab. Can you post the contents of your fstab file here?

Also, what is the correct term for the people of Ubuntu? Is it ubuntuians or ubuntonians, or something else?

---

### Post by tedrogers on 2007-06-23
Here is my fstab contents:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=[removed] /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=[removed] /media/hda5    ext3    defaults        0       2
# /dev/hda2
UUID=[removed] none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

I think either ubuntuians or ubuntonians will do! ;)

Thanks for your help....I don't undestand the fstab file at all.

---

### Post by merlinus on 2007-06-23
You need to be root to unmount the drive.
```

sudo umount /dev/hda5

```To remove the icon from your desktop:

Alt-F2
gconf-editor
apps/Nautlius/desktop

uncheck volumes_visible

And instead of:

sudo chown -R name:name /dev/hda5

try:

```

sudo chown -R name:name /media/hda5

```

since that is its mountpoint.

Good luck!

-merlin

---

### Post by tedrogers on 2007-06-23
Everything worked a treat...thanks.

---

