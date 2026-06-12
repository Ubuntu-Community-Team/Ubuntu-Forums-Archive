---
title: "boot mounts"
date: 2023-12-27
forum: General Help
---

### Post by John_Rose on 2023-12-27
Hello,

I recently installed Ubuntu 22.04.03 as dual boot with Windows 11 on a new Asus laptop. The partition structure is as follows:

```
john@John-LAPTOP-ASUS14:~$ sudo parted -l
Modèle : INTEL SSDPEKNU512GZ (nvme)
Disque /dev/nvme0n1 : 512GB
Taille des secteurs (logiques/physiques) : 512B/512B
Table de partitions : gpt
Drapeaux de disque : 

Numéro  Début   Fin     Taille  Système de fichiers  Nom                           Drapeaux
 1      1049kB  274MB   273MB   fat32                EFI system partition          démarrage, esp
 2      274MB   290MB   16,8MB                       Microsoft reserved partition  msftres
 3      290MB   77,6GB  77,3GB  ntfs                 Basic data partition          msftdata
 4      77,6GB  418GB   340GB   ntfs                 Basic data partition          msftdata
 7      418GB   452GB   34,5GB  ext4
 8      452GB   511GB   58,4GB  ext4
 5      511GB   512GB   996MB   ntfs                 Basic data partition          caché, diag
 6      512GB   512GB   273MB   fat32                Basic data partition          caché, diag
```

I have two directories in the NTFS partition Data which I have marked as favorites in GNOME (or maybe "bookmarks", not sure of the term in English, I have the French interface where they are called "signets"). After booting when I try to open one of the favorite directories I get a message that it does not exist. I then have to open Data "Other locations" ("Autres emplacements" in French) in GNOME file manager to mount it. After that I can open the favorite directories from any application without problem until shutdown.

This is annoying, could someone advise on how get the NTFS partitions mounted at boot time? Thanks so much, John

---

### Post by tea for one on 2023-12-27
Show Applications > Disks > Select Disk > Select Partition > Additional Partition Options (gear wheel icon) > Edit Mount Options
After editing then activate Mount at System Start Up

---

### Post by oldfred on 2023-12-27
While you can use Disks, its default mount options are often not the best. But you can easily change those. Either in Disks as using it, or once in fstab once the entry has been added.

I have seen this as suggested parameters:
nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0113,dmask=0022
The big_writes mount option does help performance greatly.
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix trash problems as well:

---

### Post by John_Rose on 2023-12-28
Hi tea for one,
When I call Disks I see that the two NTFS partitions are by default set to be mounted at system startup and visible in the user interface. The parameters are nosuid,nodev,nofail,x-gvfs-show

So the question is why they are not automatically loaded?

Hi oldfred,
My fstab seems to completely ignore these two partitions:

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p7 during installation
UUID=5f4446cc-f8fb-4239-975c-25ee4a540887 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=CA72-F29D  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p8 during installation
UUID=f90a7286-a15d-4012-8a59-44b8329b57ce /home           ext4    defaults        0       2

Maybe the information on my NTFS partitions is somewhere else?

Would be nice if one of you could advise on what I should do now? If I need two new fstab lines, could you please give me their precise content (including the parameters already suggested)?

Thanks so much,
    John

---

### Post by oldfred on 2023-12-28
dDisks will show or manually mount partiitons, but you have to add entries to fstab if you want them mounted on reboot.
And you must make sure Windows fast start up is off, or boot becomes really slow as mount has to timeout.

General info:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Many are older and ext4 is now used, not ext3 for example
[https://help.ubuntu.com/community/Fstab#Examples](https://help.ubuntu.com/community/Fstab#Examples)
Good examples:
[https://wiki.archlinux.org/index.php/fstab](https://wiki.archlinux.org/index.php/fstab)

Some specific NTFS examples, you have to change to your UUID. Do not use device like /dev/sdaX as that may change depending on UEFI/BIOS.
You have to create mount point, first.
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, 
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,gid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

If you want specific examples, you have to post this.
lsblk -f

---

### Post by tea for one on 2023-12-28
After creating a ntfs partition, I used Disks to automatically mount it at start up.
Disks also pops the entry in /etc/fstab.
```
/dev/disk/by-uuid/6F2E5BBE58E5BAC0 /testmnt/6F2E5BBE58E5BAC0 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```
Subsequently, I added a bookmark in Nautilus (Files)
Everything tickety-boo

---

### Post by TheFu on 2023-12-29
When I see stuff like this, I ask why?
```
/dev/disk/by-uuid/6F2E5BBE58E5BAC0 /testmnt/6F2E5BBE58E5BAC0 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

Longer isn't more descriptive and certainly a UUID is pretty useless to a human.
```
UUID=6F2E5BBE58E5BAC0     /mnt/Data     auto      nosuid,nodev,nofail,x-gvfs-show    0     0
```

UUID has been supported in fstab since 2000, perhaps earlier.  If using the UUID is the way you want to go, fine.  OTOH, I'd give the partition a label and use 
```
LABEL=Data01     /mnt/Data     auto      nosuid,nodev,nofail,x-gvfs-show    0     0
```
instead.  I'm loving the options - except for NTFS, you need a few more, like 
```
windows_names,big_writes,uid=1000,gid=1000,fmask=0002,dmask=0002
``` to keep your mount out of trouble. So the total fstab would look like:
```
LABEL=Data01     /mnt/Data     ntfs      nosuid,nodev,nofail,windows_names,big_writes,uid=1000,gid=1000,fmask=0002,dmask=0002,x-gvfs-show    0     0
```
I'm not a fan of gvfs in any way (it is big and slow), but that's a personal choice. I'd also specify the file system type, clearly.  Best to have it fail quickly if an unexpected file system showed up.

/mnt/ is for temporary administrative mounts according to the file system specs.  I wouldn't mount anything from the fstab there ... or to any location for temporary use.  I actually use /d/ as the top level to hold permanent data mounts.  Using 'df', here's how extra data gets mounted here:
```
Filesystem                               Type  Size  Used Avail Use% Mounted on
...
/dev/md1                                 ext4  1.8T  1.7T   43G  98% /raid1
/dev/md2                                 ext4  1.3T  383G  811G  33% /raid2
/dev/mapper/vg--rom01-lv--rom--data--1tb ext4  196G  125G   62G  68% /d/rom/Data/1TB
/dev/mapper/vg--rom01-lv--rom--data--r2  ext4  1.5T  383G  1.1T  27% /d/rom/Data/r2
/dev/mapper/vg--rom01-lv--rom--misc--2tb ext4  1.5T  1.4T   50G  97% /d/rom/misc/2TB
/dev/mapper/vg--rom01-lv--rom--raid      ext4  2.0T  1.7T  219G  89% /d/rom/raid
/dev/mapper/vg--rom01-lv--rom--export    ext4  196G  120G   67G  65% /d/rom/export
istar:/d/D1                              nfs4  3.5T  3.5T   47G  99% /d/D1
istar:/d/D2                              nfs4  3.6T  3.6T   50G  99% /d/D2
istar:/d/D3                              nfs4  3.6T  3.6T   28G 100% /d/D3
istar:/d/D6                              nfs4  3.6T  3.2T  224G  94% /d/D6
istar:/d/D7                              nfs4  3.6T  956G  2.5T  28% /d/D7
istar:/TV                                nfs4   98G   44G   50G  48% /TV
```
As you can see, most of the different storage goes under /d/ somewhere.  I like short, clear, paths.  The /raidX/ locations are left over from around 2005, when I didn't have nearly the level of experience that I have now.  /d/rom/ is storage that was in an old machine, since retired.  I'm slowly integrating that data into other storage. Eventually, there won't be any /d/rom/ mounts at all.

So putting all this together, I'd use:
```
LABEL=Data01     /d/Data     ntfs      nosuid,nodev,nofail,windows_names,big_writes,uid=1000,gid=1000,fmask=0002,dmask=0002,x-gvfs-show    0     0
```
to mount storage.  I don't bother with LABELs for logical volumes.  The /dev/{vgname}/{lvname} is already descriptive for me.

---

### Post by John_Rose on 2023-12-29
Hi colleagues,

I deactivated Windows fast start in BIOS but find no difference in booting or operation.

I can leave the OS partition on manual boot, so have concentrated on the Data partition. I noted that there was no mount point so created /media/Data. I then added the following line to fstab:

> UUID=0DFB17070DFB1707  /media/Data  ntfs-3g  defaults,windows_names,locale=fr_FR.utf8,uid=1000,gid=1000,fmask=0002,dmask=0002,x-gvfs-show 0 0

Now the Data partition mounts automatically and I have immediate access to the directories in it.

I did not use bigwrites since there was some discussion about its danger combined with ntfs-3g ([https://unix.stackexchange.com/questions/536971/disadvantages-of-ntfs-3g-big-writes-mount-option](https://unix.stackexchange.com/questions/536971/disadvantages-of-ntfs-3g-big-writes-mount-option)).

Thanks so much, John

---

### Post by TheFu on 2023-12-29
Be careful using anything under /media/ .  That location is prone to collision-management issues.

Problems big_writes seems to be for file systems under 4GB in size.  Any larger than that, which is the most common these days, would have ZERO concerns - well - beyond the normal warnings of using a non-native file system on Linux.  For a dual-boot system that needs to share storage between Linux and Windows, this is the least bad of bad choices.

---

### Post by tea for one on 2023-12-29
> **TheFu said:**
> When I see stuff like this, I ask why?
```
/dev/disk/by-uuid/6F2E5BBE58E5BAC0 /testmnt/6F2E5BBE58E5BAC0 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```
Defaults, other than the mountpoint.
Of course, a user can tinker with default settings to satisfy their needs, but, one would assume that default settings would be adequate.

---

### Post by TheFu on 2023-12-29
> **tea for one said:**
> Defaults, other than the mountpoint.
Of course, a user can tinker with default settings to satisfy their needs, but, one would assume that default settings would be adequate.

If only the defaults didn't suck for non-native file systems, that would be a reasonable expectation.  Sadly, we've all been burned with terrible performance, wrong ownership, wrong group, and less than great permissions with these default mounts.  gvfs and gio mounts tend to be 20-40% slower than "real mounts" are.  For convenience, they win, but if copying files is 30% slower, wouldn't you like that performance back?

I would.  Plus, gvfs and gio mounts used to place storage into odd locations in the file system. They are better at this today, but there are still times when both will conflict and break other mounts, sadly.

I just prefer to ensure automatic mounts never get used to avoid these issues.  YMMV.

---

