---
title: "fat partitions show up ugly."
date: 2006-12-27
forum: General Help
---

### Post by liniaal on 2006-12-27
since a month or something, i'm happily running ubuntu on my pc (since it saved my data, once again, actually). now what i'd like to tell you about, i have been messing around with some partitions, mostly by booting the live/install cd while ubuntu was already installed (don't know if this is bad practice? so i mention it anyway ;p)
now everything is as it should be. which is mostly fat32. everything works perfect now too, all partitions are accessible and read/writeable. only thing wrong is, 2 of the 5 fat partitions are displayed with Weird names. (like [this]("http://wie-is-je-vader.herejezus.nl/img/kut%20ubuntu.png"))
in /media the folders (which i made) do have the good name ([clarity++](http://wie-is-je-vader.herejezus.nl/img/kut%20ubuntu%202.png))

basically, what i did to add theses mounts (after deleting the old entries everywhere):
```
cd /media
sudo mkdir data
sudo mkdir games
sudo mkdir media
sudo mkdir temp

```

and for every one of those folders ```
sudo chown root:plugdev
``` and after that a ```
sudo chmod a+rwx
``` and then ```
sudo chmod o-rwx
```

well, to fix this cr*p, i followed teh steps in some other post on this forum. that means in some of the lines in fstab i replaced '/media' by '/mnt'. it didn't help. 2 of the 4 drives i changed the line of, still show up on the desktop, of which 1 has an ugly name. as a 'workaround' i disabled desktop drive icons totally, but really i would like to have my mp3 player and such automatically show up again :p

/etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=*********************************   /               ext3    defaults,errors=remount-ro 0       1
# liniaal 2 1337 2 b !false fs table
/dev/sda6	/mnt/games	vfat	defaults,users,exec,umask=007,gid=46	0	2
/dev/sda7	/mnt/data	vfat	defaults,users,noexec,umask=007,gid=46	0	2
/dev/sda8	/mnt/temp	vfat	defaults,users,noexec,umask=007,gid=46	0	2
/dev/sdb1	/mnt/media	vfat	defaults,users,noexec,umask=007,gid=46	0	2
# /dev/sda5
UUID=************************** none            swap    sw              0       0
# cdrom
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
[SIZE="1"](uid of ext3 partitions are commented out)[/SIZE]

now, my question is, of course: double u tee ef is it, i'm doing wrong?! ok everything works but i think it looks bouth ugly and immature :P.

---

### Post by zanglang on 2006-12-27
I think the names being displayed were drive volume names... they're not related to the folder name you had in /media does it?

So either you need to change the names of the disks to whichever you prefer (Still being a newbie i'm not sure where do you change that now that Edgy has remove Disk Administration from the menu... you could try Windows :p), or you could hide the Desktop icons and then create SYMLINKS directly to the /media folders and then copy them to your desktop.

---

### Post by liniaal on 2006-12-29
exactly, quite irritating if i may say so, because i was looking for it ever since i used the  live cd ;p
is there a way to install it into ubuntu anyways?

---

