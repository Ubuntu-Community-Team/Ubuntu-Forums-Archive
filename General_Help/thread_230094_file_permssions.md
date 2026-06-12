---
title: "file permssions"
date: 2006-08-05
forum: General Help
---

### Post by njzillest on 2006-08-05
I have 2 accounts on Ubuntu, njzillest (non root) and root (root acct) 

I cant log into GUI with root, I have to log in usuing njzillest, to use root, i su it. Right now, i need to access my windows partition via GUI, but njzillest (GUI) doesnt have file permissions. 

I cd to the directory and tried to change the settings using chmod. THis is hwo it looks-
```
root@root-laptop:/media/hda1# chmod +r+rw+x+w /media/hda1
chmod: changing permissions of `/media/hda1': Read-only file system

```

Is there anyway i can boot using root as GUI? if not, how can i change the permissions so njzillest can acess the windows partition using GUI. 

THanks alot in advance and have a nice day :D

---

### Post by taurus on 2006-08-05
You set the permissions for your Windows (NTFS) in /etc/fstab!  You can chmod to whatever you want because it will not work...  It has to be done in /etc/fstab!  What does your /etc/fstab look like anyway because maybe all you need is adding "umask=0222" to it...

```

more /etc/fstab

```

---

### Post by njzillest on 2006-08-05
Here is the /etc/fstab

```

njzillest@root-laptop:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0
   1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
njzillest@root-laptop:~$


```

---

### Post by taurus on 2006-08-05
Personally, I would do something like

```

/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=0222    0    0

```

---

