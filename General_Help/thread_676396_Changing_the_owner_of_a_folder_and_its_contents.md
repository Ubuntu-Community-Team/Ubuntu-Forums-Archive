---
title: "Changing the owner of a folder and its contents"
date: 2008-01-23
forum: General Help
---

### Post by lrich28 on 2008-01-23
I have all of my music on an external hard drive and when I go to change the tags on a song it tells me that I can't because I am not the owner.  The owner is root.  Is there a way I can change this?  Any help will be appreciated.

---

### Post by lluisanunez on 2008-01-23
Assuming your user was Irich28, and your music folder /media/music, do:
```
sudo chown Irich28:Irich28 /media/music -R
```

now to assign permissions:

```
sudo chmod 744 /media/music -R
```

---

### Post by lrich28 on 2008-01-23
[FONT="Arial"]My user name is landon and my root directory of the external is /media/disk.  Is there anything special I need to do for that code to work?[/FONT]

---

### Post by bodhi.zazen on 2008-01-23
Actually it depends on your filesystem

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)
[indent]Vista: Install the fs-driver using the "Windows XP compatibility mode"[/indent]

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by stchman on 2008-01-23
> **lrich28 said:**
> I have all of my music on an external hard drive and when I go to change the tags on a song it tells me that I can't because I am not the owner.  The owner is root.  Is there a way I can change this?  Any help will be appreciated.

You can also use the $USER switch.

```
sudo chown -R $USER:$USER <mount point>
```

$USER returns the user currently logged in.

---

### Post by lrich28 on 2008-01-24
Thank you guys.  I have figured it out.

---

