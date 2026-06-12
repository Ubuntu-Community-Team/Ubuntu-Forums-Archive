---
title: "I cant seem to resize a fat32 formated drive"
date: 2014-03-13
forum: General Help
---

### Post by michael114 on 2014-03-13
its an external 1 tb drive that is FAT32 gparted says this

"
File system:      fat32
size:                 931.51 GiB
Flags:

Path:                 /dev/sdb1
status:               Not mounted
label:
UUID:

first sector:       0
last sector:        1953525166
total sectors:     1953525167

(!) WARNING
cant open /dev/sdb1: no such file of directory 
cannot initialize "H:" 
mlabel: cannot initialize drive

dosfsck 3.0.12 (29 oct 2011)
dosfsck 3.0.12 29 oct 2011, FAT32,LFN

open: no such file or deirectory

Unable to read the contents of this file system!
becayse of this some operations may be unavailabe

the cause might be a smissing software package
the following list of software packages is required for fat32
file system support: dosfstools, mtools"


i had to transcribe it because i cannot select the text to copy please help thank you very much.

---

### Post by varunendra on 2014-03-14
So do you have the required packages installed as it suggests? -
> **michael114 said:**
> the cause might be a smissing software package
the following list of software packages is required for fat32
file system support: dosfstools, mtools"

Please check -
```
dpkg -l | egrep 'dosfstools|mtools'
```

If they are not installed, install them and retry.

Or maybe even better, try [**Gparted Live CD**]("http://gparted.sourceforge.net/download.php") instead of the one installed from Ubuntu repositories. The Gparted live cd usually contains the most updated version of Gparted and full support available.

---

