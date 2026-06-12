---
title: "Kubuntu always takes a long time check my filesystems during boot"
date: 2006-12-30
forum: General Help
---

### Post by Morientes on 2006-12-30
Every time I boot my kubuntu 6.10 it hangs for a moment at the fsck check of my disks. It leaves the splash screen and then it says checking file systems or something like that. It is a little annoying because it takes some time and it does it EVERY time I boot.

Any idea what is wrong?

---

### Post by wpshooter on 2006-12-30
There is a flag in a configuration file which is set wrong which is causing it to do that.

I don't know the file and it's location but I am sure you can find it if you do some searching on these forums.

---

### Post by cosmint_1973 on 2006-12-30
Look, does your Kubuntu PC shut down completely when you turn it off ? Or do you turn off your computer correctly ? Because if you have some ACPI config problems and other issues related to that your computer doesn't shut down properly and on startup it force-checks disks as drives were not correctly un-mounted on exit.

---

### Post by Morientes on 2006-12-30
No my computer shuts down like it is supposed to...

Hm, I have to see where that config file is then!

---

### Post by ajgreeny on 2006-12-30
Have a look at man tune2fs in a terminal.  This gives you a number of things you can do to your file system parameters.

If you do:-
sudo tune2fs -l /dev/hda2
in a terminal, changing the partition to suit your system, it will tell you how often the system is set up to check the file system at bootup.  To change that to a more sensible arrangement, type:-
sudo tune2fs -c60 /dev/hda2
and you will set the system to change to checking every 60 boots.  Mine is set to 80, and with the number of bootups I make this is done about once a month, (I don't leave my machine running all the time but shutdown if I won't be using it for a few hours.)

As an example, here's my output from sudo tune2fs -l /dev/hda2

sudo tune2fs -l /dev/hda2
Password:
tune2fs 1.38 (30-Jun-2005)
Filesystem volume name:   /
Last mounted on:          <not available>
Filesystem UUID:          5201864d-2b5d-4603-a2d9-1fa81a7534e5
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal filetype needs_recovery sparse_super
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              10682368
Block count:              21340344
Reserved block count:     1067017
Free blocks:              15641156
Free inodes:              10544554
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Last mount time:          Sat Dec 30 12:17:22 2006
Last write time:          Sat Dec 30 12:17:22 2006
Mount count:              10
** Maximum mount count:      80**
Last checked:             Sat Dec 23 20:54:46 2006
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
First orphan inode:       4047147
Journal backup:           inode blocks


Good luck, I hope this helps.

---

### Post by Morientes on 2006-12-30
Ok, thanks, I will try that!

---

### Post by Morientes on 2006-12-30
Strange, I get the error below when I try that...

sudo tune2fs -l /media/hde1
tune2fs 1.39 (29-May-2006)
tune2fs: Attempt to read block from filesystem resulted in short read while trying to open /media/hde1

What am I doing wrong?

Doesnt work when I type /dev/hde1 instead of /media/hde1...

Update: hm, it seems it works with some of my disks but not all? On some I get the information, but on the others I get that error!

---

### Post by Jonne on 2006-12-30
probably because it's /dev/hd**a**1 ? I'm not sure something like hde exists...

---

### Post by Morientes on 2006-12-30
...it exists....I have checked the names...

---

### Post by melancholeric on 2006-12-30
/etc/fstab

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Change the last numbers to 0 0 for partitions you think don't need to be checked every time you boot. That reduced my ubuntu boot time by minutes.

---

### Post by Morientes on 2006-12-31
Yes, I know that I can disable the check entirely, but I think that the reason it checks them every time I boot, is because there is something wrong with them. Possibly something to do with that missing superblock? Does anyone know if this might be the case and if so how I might fix it?

UPDATE: Wait I just realized, only ext-filesystems have this superblock, right? Because all the partitions where I get the error are either fat or NTFS. Hm, what might be wrong then? Why the hell does it insists on scanning the disks at every boot!

---

### Post by Morientes on 2007-01-02
bump?

---

