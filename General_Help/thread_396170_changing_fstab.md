---
title: "changing fstab"
date: 2007-03-29
forum: General Help
---

### Post by Bazzaah on 2007-03-29
I have a bit of a problem with my Edy install.

After the installation of either system upgrades or Beryl, I am no longer able to use my DVD player. I have the appropriate codecs and libraries installed. (The DVD player is though happy to play audio CDs). I think it may be something to do with Beryl as I installed Feisty to see if it would recognise my DVD and it did - I even watched a movie - but I now have the same problem after installing Beryl, though equally it may be a system update. 

I get this message when I try to mount any DVD.

mount: block device /dev/hdd is write-protected, mounting read-only

mount: /dev/hdd already mounted or /media/cdrom1 busy

mount: according to mtab, /dev/hdd is already mounted on /media/cdrom1

I have a couple of questions:

- Can someone explain to me please what this message is trying to tell me? I have seen something which suggests that I may need to change the fstab. 

- Can someone tell me please either the command lines I need to open fstab is please? 

Please say if further info is needed.

Thanks in advance.

---

### Post by nixclusive on 2007-03-29
```
mount: block device /dev/hdd is write-protected, mounting read-only
```Read only media is mounted that way.

```
mount: /dev/hdd already mounted or /media/cdrom1 busy
```When you try to remount an already mounted media this message is displayed.

```
mount: according to mtab, /dev/hdd is already mounted on /media/cdrom1
```mtab is a dynamically generated file that keeps track of mounted filesystems for the system.

by the way.. this doesn't seem to help a lot :-) What are the contents of your current fstab file? Use this command to open fstab (in read-only):```
gedit /etc/fstab
``` or maybe just paste /etc/fstab in your browser's address bar and press enter.

---

### Post by Bazzaah on 2007-03-29
here's the fstab - I'm clutching at straws here a bit and just can't figure out why I can't use my DVd player. Any ideas why I can't play DVDs?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=2a742afb-c213-459b-b960-5acef6358f70 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=35df65d2-d226-480d-a34c-cbf6799faed1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

