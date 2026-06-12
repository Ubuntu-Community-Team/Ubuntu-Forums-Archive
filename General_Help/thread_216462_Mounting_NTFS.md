---
title: "Mounting NTFS"
date: 2006-07-15
forum: General Help
---

### Post by nami on 2006-07-15
According to this site:

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

You can moust ntfs in read only mode.  But each time I try it gives me the following error:

mount: /dev/hda1 already mounted or /media/windows/ busy

any ideas?

nami

---

### Post by quedigg on 2006-07-15
Hello ,
Read this [article]("http://sourceforge.net/mailarchive/forum.php?thread_id=23836054&forum_id=2697") for more info.
Thanks

---

### Post by Unknowndeepness on 2006-07-15
Whats inside your /media/windows/ ?

---

### Post by nami on 2006-07-15
quedigg - thanks for the link, about to read it after this reply!

Unknowndeepness - it looks empty to me.  how do i check for hidden or system files in that folder?

---

### Post by jaimz on 2006-07-15
you might want to try the way I was told
it worked for me

[http://www.ubuntuforums.org/showthread.php?t=216316]("http://www.ubuntuforums.org/showthread.php?t=216316")

just scroll down and you'll see the steps

---

### Post by nami on 2006-07-15
> **jaimz said:**
> you might want to try the way I was told
it worked for me

[http://www.ubuntuforums.org/showthread.php?t=216316]("http://www.ubuntuforums.org/showthread.php?t=216316")

just scroll down and you'll see the steps

I just tried that and it gave me the following error when i did "sudo mount -a"

> nami@nami-desktop:~$ sudo mount -a
mount: /dev/hda1 already mounted or /mnt/Windows busy
mount: according to mtab, /dev/hda1 is mounted on /
nami@nami-desktop:~$

So I commented out the original /dev/hda1 line from fstab and was left with
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /mnt/Windows  ntfs    nls=utf8,umask=0222 0       0

I tried mounting again and I got the same error again???

Am I supposed to be using hda2 or something?

---

### Post by givré on 2006-07-15
It seams that /hda1 is your linux partition, not your windows partition. Uncomment it in /etc/fstab or you will have some surprise on reboot :cool: 
So to know what is your NTFS patition, do
```
sudo fsdisk -l
```

---

### Post by nami on 2006-07-15
> **givré said:**
> It seams that /hda1 is your linux partition, not your windows partition. Uncomment it in /etc/fstab or you will have some surprise on reboot :cool: 
So to know what is your NTFS patition, do
```
sudo fsdisk -l
```

Thanks for the uncommenting tip! :D

sudo fsdisk -l says "command not found" ?

---

### Post by givré on 2006-07-15
yeh, stupid typo :cool: ; Here it will be better
```
sudo fdisk -l
```

---

### Post by jaimz on 2006-07-15
I got that busy thing too

all I did was reboot
and everything worked out fine

---

### Post by nami on 2006-07-15
THanks

its hdb1 instead of hda1 ](*,) 

Anyway I made the change in the fs file and then tried mounting again and it said
> 
mount: /dev/hdb1 already mounted or /mnt/Windows busy
mount: according to mtab, /dev/hdb1 is mounted on /tmp/disks-conf-hdb1

so I went to that directory and all the files from the ntfs hdd were already there ??? Whats going on, don't i have to mount it?  If not why can I not click on the hard drive icon from the computer menu in "places" ???

---

### Post by givré on 2006-07-15
Come on guys, you should not reboot if you comment your root line in /etc/fstab
Don't comment lines in fstab, just make them better.

---

### Post by givré on 2006-07-15
```
sudo umount -a
sudo mount -a
```
and you will be ok

EDIT: after closing any nautilus windows or whatever looking at /tmp/*

---

### Post by nami on 2006-07-15
Thanks!

---

