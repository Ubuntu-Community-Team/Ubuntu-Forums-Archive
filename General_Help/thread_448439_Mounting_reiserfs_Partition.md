---
title: "Mounting reiserfs Partition"
date: 2007-05-19
forum: General Help
---

### Post by foxmulder881 on 2007-05-19
If I have another partition on a different hdd which is in reiserfs format, how do I read the reiserfs partition contents within Ubuntu?

---

### Post by Herman on 2007-05-19
Hello foxmulder881,
You have to 'mount' it.
Before you can do that you need to know what it's called in Linux, (the disk and partition number), for example, /dev/hda2 or something like that. You can find that out by looking with GParted or any partitioning program. fdisk is a good one, 'sudo fdisk -lu' 
Make a mount point, you can name it whatever you like, I'll call mine 'ubuntu'.
```
sudo mkdir /media/ubuntu
```Mount the filesystem
```
sudo mount -t reiserfs /dev/hda2 /media/ubuntu
```Then you should have an icon on your desktop you can open and see your files. If not, go to your /media folder and open it there instead.
Regards, Herman :)

---

### Post by foxmulder881 on 2007-05-19
Thanks Herman, I'll give it a shot.

UPDATE: How do I get it to automatically mount on system startup?

---

### Post by Herman on 2007-05-26
Hello foxmulder881,
If you want other partitions to be mounted automatically during boot-up, the normal way most people do that is by making an entry for them in our /etc /fstab files.

Actually I don't bother to mount my other file systems in /etc/fstab any more myself. I think a better idea would be just just make a script for mounting extra partitions with, here's my link on that, [Making a script for mounting your other filesystems instantly]("http://users.bigpond.net.au/hermanzone/p10.htm#Make_a_mounting_script")

But if you really want  to do it the /etc/fstab way, here is a link to [tuxfiles how to edit and understand /etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html").  If you read that it will explain it very well. Basically, I would suggest adding a line similar to this one, 
```
/dev/hda3      /media/mountpoint reiserfs defaults       0      2
```Where 'dev/hda3' is your reiserfs partition and 'mountpoint' is the name of a directory in /media you made for mounting it in. Something like that should work , but I just made that line up, I haven't tested it yet.

In Ubuntu it's a little bit more complicated than described in that article because we use file system 'UUID' numbers now to specify our file systems. 
         [                          About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with"). That means you would add  lines something like this now,
 ```
#/dev/hdb4
UUID=237f0cef-9905-41fb-82ba-bc360fb43a25 /media/mountpoint reiserfs defaults  0    2
```Try that and see if it helps you.
If you need more help you can post a copy of your output from 'blkid', and also your /etc/fstab file. here I might be able to give you more specific help with it to suit your particular system.

Regards, Herman :D

---

