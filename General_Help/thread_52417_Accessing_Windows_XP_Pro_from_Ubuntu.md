---
title: "Accessing Windows XP Pro from Ubuntu"
date: 2005-07-27
forum: General Help
---

### Post by fmcdee on 2005-07-27
I want to view and access (if possible), copy file from EX Pro to Ubuntu if possible.  Can this be done?  How?  Thanks O:)

---

### Post by crispingatiesa on 2005-07-27
R U talking accesing files in a network or in adual boot system?

---

### Post by Omnios on 2005-07-27
Check out 

[Unofficial Ubuntu Starters Guide](http://ubuntuguide.org/#windows) 

 Your windows drive will probably ntfs so you can mount it as such for read access. Currently there is no real safe way to write to ntfs format (XP's format)

---

### Post by souki on 2005-07-27
if you mean "accessing the windows partition on a dual boot system"

you have to mount the windows partition, this can be done by editing the /etc/fstab file
```
/dev/hda2       /media/windows    vfat    noauto,user,umask=000    0       0
```where /dev/hda2 is the windows partition and /media/windows the mount point
note that my xp partition is fat formated. If you have a ntfs partition try to change 'vfat' with 'ntfs' (can't try).
if you want your partition to be mounted at boot, remove the 'noauto' flag

next, the partition can be mounted with
```
mount /media/windows
```

---

