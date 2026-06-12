---
title: "using fat32 drive to share files with XP"
date: 2005-05-18
forum: General Help
---

### Post by byen on 2005-05-18
Hey guys,
I   am a newbie and i really need this help!!! I partitioned my HD into 3 parts..C -Ntfs, D Fat32 and E for linux.... I read somewhere that files on fat32 can be opened from the linux browser when i try to do it it gives me an error saying 
Could not mount device.
The reported error was:
mount: can't find /dev/hda5 in /etc/fstab or /etc/mtab


Anyway i can fix this to access files in that drive? please suggest....thank you.

---

### Post by mirtux on 2005-05-18
Hi,
 you have first of all to mount it.... Well you have to look up which device contains your fat32 partition, let's say /dev/hda3. Create the mount point with
 ```
sudo mkdir /media/fat32 
``` 
then issue a 
 ```
sudo mount /dev/hda3 /media/fat32
``` 
You can access your partition in /media/fat32 directory.

That's all. Hope this helps,
Regards,
MC

---

### Post by kiddyfurby on 2005-05-18
you can add a line to /etc/fstab to have the partition auto mounted on boot

/dev/hda5	/media/storage	vfat	rw,user,umask=0,iocharset=utf8	0	0

you don't need iocharset=utf8 unless you have CJK filenames

I suppose /dev/hda5 is your FAT32 partition, you can find it out by
sudo fdisk -l

/media/storage is the mount point (the folder to mount the partition to)
it can be somewhere else but you have to create the folder with
sudo mkdir [full path of folder]
first

---

### Post by byen on 2005-05-18
thank you guys. Got it! Ive started learning linux and hope would someday be able to help someone too! :)

---

### Post by Tails747 on 2005-05-18
I have Windows ME, with one partition for Windows and all it's files, one almost as big for Linux, and a really small one for that swap file thing. :P would I do anything differently to gain access to the windows partition in Linux? "this would still allow me to USE windows, right?"

---

### Post by shakin on 2005-05-18
[QUOTE=Tails747]I have Windows ME, with one partition for Windows and all it's files, one almost as big for Linux, and a really small one for that swap file thing. :P would I do anything differently to gain access to the windows partition in Linux? "this would still allow me to USE windows, right?"[/QUOTE]

Same thing and it won't harm Windows unless you start deleting Windows system files while in Linux :)

running 'sudo fdisk -l' will list your partitions so you can find which one you need (probably /dev/hda1), then just mount it as shown above.

---

