---
title: "Can't download files to FAT32 filesystem"
date: 2007-01-25
forum: General Help
---

### Post by v8YKxgHe on 2007-01-25
Hey,

I'm having some trouble downloading files to a FAT32 file system. I use a spare 80gb hard drive formated as FAT32 to share files between Windows and Linux, however I can not download files directly to the FAT32 hard drive, when ever I do they always end up as 0kb in size. But when I download them to my home directory of my main hard drive, they download fine. 

I have read/write access to the FAT32 drive, but I just can't seem to download files to it. I'm using Firefox, haven't tried other browsers to see if they have the same problem. Why is this?

---

### Post by taurus on 2007-01-25
Have you tried copying the download file from your $HOME to that fat32 drive?

---

### Post by v8YKxgHe on 2007-01-25
Yep, works fine that way - it's just a pain that it wont download to it.

---

### Post by benerivo on 2007-01-25
Have you tried using the DownLoadThemAll extension to Firefox? It is a download manager that works inside Firefox, and will start downloads with a couple of clicks (just as a normal download in Firefox does). The important differnce is that it does not save directly to the destination folder, but rather stores the partial download in its own folders then when complete transfers it to your own location (in your case, the FAT32 drive). In practical terms the users sees no difference whatsoever and downloads files in the same way they would normally.

---

### Post by fsando on 2007-01-29
I have downloading to fat32 working - I used this in /etc/fstab:

```
/dev/sda5  /home/<user name>/f32dat     	vfat    defaults,utf8,umask=000,gid=46
```Two things (not sure if both are important, probably the umask is doing the trick):
1. Mounted the drive  in my home folder (created a subfolder 'f32dat').
2. changed umask: 'umask=000'

I believe 'umask=000' gives everybody read/write access to the drive. But when it is mounted in my home folder it gets restricted to me (and root).

I still sometimes have problems with firefox and downloading - but they must be with firefox misinterpreting the server response (it happens when the download is initiated through a script - ie. the d/l link is not pointing directly to the file)

EDIT:
The problem reoccurred - and persists. Workaround: right-click **Save Link As**. 
Maybe remove possibly offending characters (international characters, spaces etc.).

---

### Post by croatcatala on 2007-05-18
I've got the same problem that appears on this thread, but cannot see how to solve it. Does anybody have had this solved?

---

### Post by taurus on 2007-05-18
Can you post

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by croatcatala on 2007-05-18
> **taurus said:**
> Can you post

```
sudo fdisk -l
cat /etc/fstab
```


```
sudo fdisk -l
```
Disc /dev/sda: 200.0 GiB, 200049647616 octets
255 capçals, 63 sectors/pista, 24321 cilindres
Unitats = cilindres de 16065 * 512 = 8225280 octets

Dispositiu Arrenc.   Comença       Acaba    Blocs    Id  Sistema
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       24133    59641312+  83  Linux
/dev/sda3           24134       24321     1510110    f  W95 estesa (LBA)
/dev/sda5           24134       24321     1510078+  82  Linux swap / Solaris

Disc /dev/sdb: 60.0 GiB, 60022480896 octets
255 capçals, 63 sectors/pista, 7297 cilindres
Unitats = cilindres de 16065 * 512 = 8225280 octets

Dispositiu Arrenc.   Comença       Acaba    Blocs    Id  Sistema
/dev/sdb1   *           1        7296    58605088+   b  W95 FAT32
/dev/sdb2            7297        7297        8032+   f  W95 estesa (LBA)
/dev/sdb5            7297        7297        8001    1  FAT12

```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8c9545cf-5557-4825-8c4d-35907b7b31dc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=4188-1399  /mnt/petit      vfat    defaults,utf8,umask=000,gid=46 0       1
# /dev/sda1
UUID=1220091520090209 /mnt/windowsxp  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=743df673-49b9-4687-a8a1-d6d662812195 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2007-05-18
Are you talking about /dev/sdb1?

```
# /dev/sdb1
UUID=4188-1399 /mnt/petit vfat defaults,utf8,umask=000,gid=46 0 1
```

---

### Post by croatcatala on 2007-05-18
> **taurus said:**
> Are you talking about /dev/sdb1?

```
# /dev/sdb1
UUID=4188-1399 /mnt/petit vfat defaults,utf8,umask=000,gid=46 0 1
```

I'm sorry, Taurus. Yes, that's right, /dev/sdb1, which is mounted on /mnt/petit, is the one who fails.
It had "umask=007", I changed it to umask=000 as I saw somewhere, but it still fails after rebooting.

---

### Post by taurus on 2007-05-18
What if you edit /etc/fstab and change it to
   
```
/dev/sdb1    /mnt/petit    vfat    iocharset=utf8,umask=000    0    0
```
Save it and reboot.  Now, see if you can write to /mnt/petit.

---

### Post by croatcatala on 2007-05-18
> **taurus said:**
> What if you edit /etc/fstab and change it to
   
```
/dev/sdb1    /mnt/petit    vfat    iocharset=utf8,umask=000    0    0
```
Save it and reboot.  Now, see if you can write to /mnt/petit.

Doesn't work.
In fact, I do can write to /mnt/petit, through any program but Firefox. And even when using right-click and "Save to...", it works properly. But when using some scripts (a.e, Gmail "Download" option), it downloads but the resultant file has a size of 0 bytes (and it contains nothing, don't need to say) just when downloading to FAT32 drive. If I download this way to any other partition, everything is OK.

---

### Post by croatcatala on 2007-05-23
Nobody can help? I'm absolutely lost about where to find an answer.

---

### Post by v8YKxgHe on 2007-05-23
I've just tried writing to my Fat32 hard drive again now that I have feisty ... but nope, it's not having it!

---

