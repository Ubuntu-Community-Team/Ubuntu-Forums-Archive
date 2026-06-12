---
title: "Filesystem help..."
date: 2007-06-20
forum: General Help
---

### Post by Brother Dysk on 2007-06-20
Hello. I've just installed 7.04 and updated it, and seem to have an issue. I can access all my ntfs partitions fine (hda1, hdb1, hdc1 - ubuntu is on hdb2) except for one folder in hdc1 - my forty or so gig Music folder and all of its subfolders. Browsing to it gives an error. Also, the disk size for hdc1 is reported as 80-odd gigs, when it should be 120-odd, disconcertingly matching the size of the inaccesible folder...

Any suggestions?

---

### Post by rishabh on 2007-06-20
Go to a terminal and type the following:

```
cat /etc/fstab
```

Paste the output here. It might help.

Also paste the output of 

```
fdisk -l
```

---

### Post by finer recliner on 2007-06-20
^ paste the output of
```
sudo fisk -l
```
that will give you a more complete list of your recognized drives.

---

### Post by rishabh on 2007-06-20
To "finer recliner"

Actually, I've never heard of the "fisk" command. Are you sure you didn't mean "fsck" or "fdisk"? I've already mentioned "fdisk". As for fsck, it's not going to help. [-X

---

### Post by Brother Dysk on 2007-06-20
fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=a0fb7400-0d15-4e03-a403-feba27baced6 /               reiserfs notail          0       1
# /dev/hda1
UUID=7A688F04688EBE7F /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=8C2098F92098EC08 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=e76a2f88-10df-45bd-a452-95c5bc6cfa9a none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

fdisk -l (as root)
```
Disk /dev/hda: 10.1 GB, 10110320640 bytes
255 heads, 63 sectors/track, 1229 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1228     9863878+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7127    57247596    7  HPFS/NTFS
/dev/hdb2            7128        7189      498015   82  Linux swap / Solaris
/dev/hdb3            7190        9729    20402550   83  Linux

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14946   120053713+  42  SFS

```

...and the specific error when running ls in the offending directory
```
frans@frans-linux:/media/disk/Music$ ls
ls: reading directory .: Input/output error

```

Thank you for your help :)

---

### Post by finer recliner on 2007-06-20
yes im sorry for the typo. i meant fdisk. 

```
sudo fdisk -l 
```

the important part was adding sudo.

---

### Post by Brother Dysk on 2007-06-20
I did in fact run fdisk as root. I see that it is noting the problem partition (hdc1) as SFS rather than NTFS - what does that mean?

---

### Post by Brother Dysk on 2007-06-20
Is there really no-one who can offer any solutions or advice? This is as good as making the OS useless for me...

---

### Post by rishabh on 2007-06-21
Sorry for the late reply. 
As far as I can make out, you have three hard drives:
[LIST=1]
[*] /dev/hda: 10.1 GB
[*] /dev/hdb: 80.0 GB
[*] /dev/hdc: 122.9 GB
[/LIST]
And /dev/hdc1 is the drive you want.

According to you fstab, /dev/hdc1 is not even mounted. So try this:
```
sudo mkdir /mnt/a
```
You can replace "a" with anything you like.
```
mount /dev/hdc1 /mnt/a
```
That manually mounts the drive to "/mnt/a". then:
```
cd /mnt/a
ls
```

If that doesnt work, you should try
```
umount /dev/hdc1
```
BEFORE mounting it to /mnt/a, just incase it's improperly mounted elsewhere.

---

### Post by Brother Dysk on 2007-06-21
Unfortunatly, I got the exact error I was expecting, by doing this. Here's the terminal transcript:
```
$ sudo mkdir /mnt/a
Password:
$ mount /dev/hdc1 /mnt/a
mount: only root can do that
$ sudo mount /dev/hdc1 /mnt/a
mount: you must specify the filesystem type
```

And when specifying ntfs:
```
$ sudo mount -t ntfs /dev/hdc1 /mnt/a
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Also, it was mounted on first boot - though you are right in saying that it isn't now - and the ntfs configuration tool refuses to mount it...

If I go to Places -> Computer in the applications menu (GNOME) there is a "85.2GB Volume" which is what accessed the partition before, on initial boot (though the 40GB folder was strangely not working, which coincides with the underestimation of volume size). Double-clicking it lets me know that I don't have privileges to mount the drive.

Thanks for the suggestions, though :) Help?

---

### Post by kuja on 2007-06-21
Brother Dysk: You didn't use the "compress" or "encrypt" options on those folders in windows did you? Bear in mind that Linux won't be able to read those AFAIK.

---

### Post by rishabh on 2007-06-21
Well, your fstab says:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       14946   120053713+  42  SFS
```

It says your FS type is "SFS".
Can you access it on Windows?
Does it work if you try to mount it on the LiveCD?

---

### Post by Brother Dysk on 2007-06-21
Neither encrypted nor compressed, no.

And yes, I can access it from Windows, it treats it as a normal NTFS partition (I have no idea why the fstab calls it SFS). One the LiveCD, the situation was as on first boot - partition mounted, but only as a around 80 gig volume, when it ought to be around 120 gigs, and the music folder was not functioning. Now it refuses to mount at all, it seems...

---

### Post by Brother Dysk on 2007-06-26
Well I really don't know what the problem is (the partition doesn't show up in the "Places -> Computer" menu anymore...) but if someone could help me fix it, I would be most grateful...

---

### Post by Brother Dysk on 2007-06-26
Aha, I think a part of the reason would be that the disk in question is formatted as a dynamic disk, and the partition in question is a spanned volume, across two volumes on the same disk (why anyone would set it up like that I cannot fathom, but the disk was a hand-me-down)...

Any help?

(EDIT: It seems that a /dev/hdc2 also exists, despite fdisk not showing it - this mounts, but with an unreadable directory (presumably stored on the /dev/hdc1 volume which it is spanned to in Win2k)

---

### Post by Entity` on 2007-06-26
How old is your hard drive?

This might be a long shot, but maybe your disk is failing.

As for dynamic disks spanning multipule volumes, I never tried it and don't want to because it looks like it would give me headaches.  Get into windows, move your data, and redo your disks.  Your second option is to use Partition Magic 8.0.

---

### Post by Brother Dysk on 2007-06-26
The disk isn't actually that old, and still works perfectly fine from Windows. I odn't have space to do a temporary backup to restore the drive to a sane partition scheme, unfortunatly, and PartitionMagic doesn't seem to recognise the Dynamic Disk as anything other than an unidentifiable partition.

I am getting to be convinced that the crux of the problem is the fact that the volume is a spanned one, comprised of two seperate volumes on the same disk.

---

