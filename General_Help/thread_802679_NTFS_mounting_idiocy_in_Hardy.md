---
title: "NTFS mounting idiocy in Hardy"
date: 2008-05-21
forum: General Help
---

### Post by Lime84 on 2008-05-21
The way Hardy Heron handles NTFS volumes is really starting to get on my nerves. Every time I want to listen to MP3s from my Windows partition I have to click on it's icon so it would actually mount. But the real problem is: if you have two partitions, you have to click them in the same order every time, otherwise you're gonna have to re-add all your media because the partition's mount point depends on the order you mount it in.

Technically, this is not a problem as I know the solution all to well, but I'm really curious if there's a way to do this without messing with fstab as Ubuntu is supposed to be a "newbie" system and setting mount points and read/write privileges in fstab is far from that...

---

### Post by Victormd on 2008-05-21
From what I understando, the only way is through fstab. Gutsy did this automatically, I don't know why it changed in hardy...

When you boot into ubuntu, even though you don't have your ntfs partitions on the desktop, they should be listed in the menu "Places". If you want to leave the same mount point as the ubuntu default, browse to your media folder (or in the terminal type cd /media then ls) and look at the mountpoint given to your ntfs partition (i.e. folder called backup - in my case).

from the terminal, type
```
sudo fdisk -l
```
this will list all your partitions. This is what my looks like.
> 
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

Device Boot Start End Blocks Id System
/dev/sda1 * 1 2550 20482843+ 7 HPFS/NTFS
/dev/sda2 2551 4400 14860125 83 Linux
/dev/sda3 4401 4462 498015 82 Linux swap / Solaris
/dev/sda4 4463 9725 42275016 7 HPFS/NTFS
So from this list, I know I want to mount /dev/sda1 and /dev/sda4

from the terminal type
```
sudo gedit /etc/fstab
```

this will open your fstab. Let's say I wanted to mount my /dev/sda1, then I would add this to the last line:
> 
/dev/sda1 /media/backup ntfs defaults,umask=007,gid=46 0 1
This will mount /dev/sda1 in the /media/backup folder (as explained above)
simply keep adding lines as you need more partitions. Save your fstab and reboot. You should now get the partitions automatically mounted and the respective icons on your desktop.

An alternative is to add a line to the end of fstab using the UUID option instead of /dev/sda1. You can determine the UUID by using (i.e., for sda1)
```
sudo vol_id -u /dev/sda1
```
so your fstab file will have this line
> 
UUID=NUMBER_ID /media/backup ntfs defaults,umask=007,gid=46 0 1
where NUMBER_ID is the output from vol_id for your device, i.e.:
[/quote]UUID=78980E1B980DD890 /media/backup ntfs defaults,umask=007,gid=46 0 1[\quote]
instead of
> /dev/sda1 /media/backup ntfs defaults,umask=007,gid=46 0 1
I found this to be more stable/suitable than using the /dev/sda1 option.

---

### Post by Lime84 on 2008-05-21
> **Victormd said:**
> 

When you boot into ubuntu, even though you don't have your ntfs partitions on the desktop, they should be listed in the menu "Places". If you want to leave the same mount point as the ubuntu default, browse to your media folder (or in the terminal type cd /media then ls) and look at the mountpoint given to your ntfs partition (i.e. folder called backup - in my case).



Well that's the whole point, the only way to have your partitions mount at startup is adding them to the fstab file. Otherwise, they won't get mounted until you click on them in the gnome menu. Does anyone know the reason behind this "feature" ?

---

