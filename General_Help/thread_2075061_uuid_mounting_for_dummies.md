---
title: "uuid mounting for dummies?"
date: 2012-10-22
forum: General Help
---

### Post by opfeld on 2012-10-22
So I have read through [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
as well as 
[http://forums.linuxmint.com/viewtopic.php?f=42&t=22093](http://forums.linuxmint.com/viewtopic.php?f=42&t=22093)

and I just can't seem to figure out how to mount a partition using UUID.  I want to do this because sometimes during start I get the error unable to mount "so-so" press S to skip or M for manual mounting.  I have a partition, ext4, named Data and usually it is mounted under /media/Data, which is just what I want.  Can anyone give a very simple explanation for how to accomplish this?

I have tried using PsyDM and while it usually works I still get that error sometimes.

---

### Post by pqwoerituytrueiwoq on 2012-10-23
sure you don't want it in /mnt ? then symlink to it 
/mnt will not show up in places or on the desktop
just add a line like this to /etc/fstab
```
UUID=1ef3d0e2-d14f-4ffb-81af-e27175edb0f6 /mnt/windows    ext4    defaults        0       2
```if anyone is wondering
/mnt/windows contains a vdi file for virtualbox
i get my uuid with gparted
[[IMG]http://www.zimagez.com/miniature/screenshot-10232012-124400am.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-10232012-124400am.php")[[IMG]http://www.zimagez.com/miniature/screenshot-10232012-124441am.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-10232012-124441am.php")

---

### Post by ~LoKe on 2012-10-23
In the terminal, type:
```
sudo blkid
```
It'll give you a list of your drives and their UUID.  For example, here's is my 750GB NTFS hard drive labeled "Storage".
> /dev/sdb1: LABEL="Storage" UUID="AA7A6B347A6AFD07" TYPE="ntfs"

So, I know my UUID is **AA7A6B347A6AFD07**

To make that mount to where I want it, I'd do this:

```
gksu gedit /etc/fstab
```
And add this at the bottom...
> UUID=AA7A6B347A6AFD07 /media/Storage               ntfs    errors=remount-ro 0       1
Save and reboot.


If you'd like help getting that to work, post the output of 
```
sudo blkid
```
and we can go from there.

---

### Post by opfeld on 2012-10-23
here is the drive I am trying to have automount at boot

/dev/sdb3: LABEL="Data" UUID="0c750c53-6169-438c-925b-8cf024ce3fa3" TYPE="ext4"

I am not particular to where it is mounted just that it is mounted without fail everytime I boot up the computer.

the two portions you guys are using "/media/Storage" and "/mnt/windows"  are those just something you make up or do they have more significance

---

### Post by nothingspecial on 2012-10-23
Unmount the partition

Make a folder

```
sudo mkdir /media/Data
```

back up fstab

```
sudo cp /etc/fstab /etc/fstab_bak
```

edit fstab

```
gksudo gedit /etc/fstab
```


put this line at the end

```
LABEL=Data /media/Data  ext4   defaults                       0       0

```

save, close then check it works

```
sudo mount -a
```

That's it.

---

### Post by opfeld on 2012-10-23
thanks that looks like it worked, just for my own clarification purposes, when I do mkdir /media/Data am I just creating a mount point and how much creative license do I have with that?  Could I do mkdir /movies or /pictures ?

---

### Post by drmrgd on 2012-10-23
> **opfeld said:**
> thanks that looks like it worked, just for my own clarification purposes, when I do mkdir /media/Data am I just creating a mount point and how much creative license do I have with that?  Could I do mkdir /movies or /pictures ?

You have as much creative license as you like.  That is, the name of the mount point could just about be anything (special characters would probably cause you a little grief, though).  As long as you direct a mountable partition to that mount point with an fstab entry, you can call it whatever you like.

---

### Post by JKyleOKC on 2012-10-23
> **opfeld said:**
> thanks that looks like it worked, just for my own clarification purposes, when I do mkdir /media/Data am I just creating a mount point and how much creative license do I have with that?  Could I do mkdir /movies or /pictures ?As drmrgd said, you can make the directory anywhere in the tree that you want. However there's one "automagic" thing about using a subdirectory in "/media" that is different from all other locations: devices mounted under "/media" show up automagically in the file manager (Places) while those put anywhere else do not, so you have to look for them in "File System" or take extra steps to create launcher icons for them. That's why most advice given here always suggests using "/media" as the topmost directory.

---

### Post by dcstar on 2012-10-23
> **opfeld said:**
> 
.......
the two portions you guys are using "/media/Storage" and "/mnt/windows"  are those just something you make up or do they have more significance

/media is a System folder and should **never, ever** be used for fstab mounts as the system assumes it has total control of all entries in that folder for mounting removable devices.

/mnt is the recommended place for permanent user mount points, or you can create your own (using sudo) anywhere outside of any Linux System folders.

---

