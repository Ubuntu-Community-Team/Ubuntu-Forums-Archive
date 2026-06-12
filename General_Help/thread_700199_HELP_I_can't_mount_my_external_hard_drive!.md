---
title: "HELP I can't mount my external hard drive!"
date: 2008-02-18
forum: General Help
---

### Post by dingo_502 on 2008-02-18
sudo fdisk -l

Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4982     1686825    5  Extended
/dev/hda5            4773        4982     1686793+  82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x947bfcce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

---

### Post by richardjennings on 2008-02-18
is /dev/sda the external drive?

what problems are you having with mounting the drive? I

---

### Post by dingo_502 on 2008-02-18
yes sda is my external hard dive

---

### Post by dingo_502 on 2008-02-18
I tried to boot the computer in windows and safly remove it...I even got on my other linux system and unmounted it....I am lost.

---

### Post by dingo_502 on 2008-02-18
When I try to mount it I get this message:

hal-storage-removable-mount-all-options refused uid 1000

---

### Post by geo909 on 2008-02-18
So you mean that everybody sees the disk except Ubuntu?
Be a little more specific..

BTW have you added a line about sda in your /etc/fstab file or something?

---

### Post by richardjennings on 2008-02-18
what happens if you try:

```
sudo mkdir /media/disk
sudo mount /dev/sda /media/disk
```

if no errors, cd into the directory to see whats in there.

cd /media/disk
ls

---

### Post by dingo_502 on 2008-02-18
sudo mkdir /media/disk
mkdir: cannot create directory `/media/disk': File exists
dingo@Media-Computer:~$ sudo mount /dev/sda /media/disk
mount: you must specify the filesystem type

This is what I get when I do that. 

This is an external hard drive that has ntfs file system on it. I I had to force mount it on another computer before for it to work and I can't seem to remember the command to force mount the thing.

Does anyone know the line to use?

---

### Post by geo909 on 2008-02-18
What about
```
sudo mount -t ntfs /dev/sda /media/disk
```
Does it mount, then?


If not, I also think that there is a tool, "ntfs-3g" that may do the job:
```
sudo apt-get update
sudo apt-get install ntfs-3g
```
Then:
```
mount -t ntfs-3g /dev/sda /media/disk     
```

If not..
Hmmm..
Just an idea: Is that a Seagate FreeAgent 500 GB drive?!

---

### Post by Yellow Pasque on 2008-02-18
geo909, close..

```
sudo mount -t ntfs-3g -o rw,auto,user,exec,uid=1000 /dev/sda1 /media/disk
```

---

### Post by Wiebelhaus on 2008-02-18
> **geo909 said:**
> What about
```
sudo mount -t ntfs /dev/sda /media/disk
```
Does it mount, then?


If not, I also think that there is a tool, "ntfs-3g" that may do the job:
```
sudo apt-get update
sudo apt-get install ntfs-3g
```
Then:
```
mount -t ntfs-3g /dev/sda /media/disk     
```

If not..
Hmmm..
Just an idea: Is that a Seagate FreeAgent 500 GB drive?!


We also must not forget to mention that if the windows partition was not shut down properly then your ntfs log file will be flagged as dirty and Ntfs-3g will not mount it automatically because there's a chance it could damage something , A very slim chance by the way nothing to worry about , if the log file is dirty you will have to mount it with

"-o force" option.

---

