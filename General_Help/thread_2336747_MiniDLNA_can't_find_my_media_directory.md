---
title: "MiniDLNA can't find my media directory"
date: 2016-09-10
forum: General Help
---

### Post by Matt_Dyck on 2016-09-10
My media is stored on a separate partition from my Ubuntu 16.04 OS. It is set to auto-mount on startup and is on device sda5. When using **mount** in terminal, it shows that dev/sda5 is on /mnt/Media. I've tried both of those as "paths" in the /etc/minidlna.conf file and neither works (as you can see below). I'm kind of a noob to this stuff and am learning as I go, so if you can explain things simply that would be amazing. Thanks.
```
matt@MusicMaker2:~$ sudo minidlnad -R[sudo] password for matt: 
[2016/09/10 16:13:24] minidlna.c:624: error: Media directory "P, /mnt/Media/Pictures" not accessible [No such file or directory]
[2016/09/10 16:13:24] minidlna.c:624: error: Media directory "V, /dev/sda5" not accessible [No such file or directory]
[2016/09/10 16:13:24] minidlna.c:624: error: Media directory "A, /dev/sda5" not accessible [No such file or directory]

```

Update:
I tried with the local directory of my pictures "/home/matt/Pictures" and that says "not accessible". Would that mean this is a permissions issue?

---

### Post by DuckHook on 2016-09-11
The classical way to automount a partition at startup is to edit the *fstab* file which the OS will always read and execute. I am not familiar with method that you have used. Instructions for *fstab* are below:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you wish the partition to automount *only when you need it*, a more sophisticated and involved method is *autofs*. Instructions for *autofs* are below:

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by Matt_Dyck on 2016-09-11
It's not the auto-mount I'm having trouble with. I already have that set up fine. It's just the program MiniDLNA which says that any directories I have are unable to be accessed. I'm trying to use minidlna to share media across my home network, but because the program says "not accessible (No such file or directory)" I assume it doesn't have the right permissions or something? Anyway, I hope I made that a bit more clear.

---

### Post by DuckHook on 2016-09-11
Ah. My bad.

I am completely unfamiliar with MiniDLNA so am afraid you will have to await response from a more knowledgeable poster. Sorry for the misunderstanding.

---

### Post by Keith_Helms on 2016-09-12
First of all /dev/sda5 is a device not a directory.  It is not a path you would supply to any application.

If you're sure that partition is being correctly mounted at started, what does the following show?
```
ls -l /mnt/Media
```

Depending on how you're mounting the partition, you might wind up with the name of the partitions as part of the path.  For example, when I mount an USB external hard drive it might show up as /media/keith/My Passport.  You might find there's an extra level to the path that you have to account for, such as **/mnt/Media/*partitionname*/Pictures**

---

### Post by Matt_Dyck on 2016-09-12
```
matt@MusicMaker2:~$ ls -l /mnt/Mediatotal 3036
drwxr-x--- 1 matt matt    8192 Aug 23 18:07 Documents
drwxr-x--- 1 matt matt    4096 Jan  4  2016 Downloads
drwxr-x--- 1 matt matt       0 Apr  3 12:10 found.000
drwxr-x--- 1 matt matt   65536 Aug 29 19:41 Music
drwxr-x--- 1 matt matt    4096 Jul  4 17:27 Pictures
drwxr-x--- 1 matt matt       0 Nov  6  2015 $RECYCLE.BIN
drwxr-x--- 1 matt matt       0 Nov  6  2015 System Volume Information
drwxr-x--- 1 matt matt   12288 Sep  5 16:41 Videos
```
This is what is shown for that. I figured that dev/sda5 was the device, but just tried it anyway since the other path hadn't worked. The partition that gets mounted is called "Shared Partition", and I think I already tried adding that in, but I'll try again just in case I didn't.

---

### Post by Matt_Dyck on 2016-09-12
Still no luck. I've even tried with home/matt/pictures and it says the same thing.

---

### Post by Matt_Dyck on 2016-09-12
I'm trying to change the permissions now, but chmod doesn't seem to work. I think it has something to do with the fact it's a NTFS drive (forgot about that). So hopefully I can even figure this out myself, I'll let you know.

---

### Post by Matt_Dyck on 2016-09-12
I switched over to Windows to change permissions on the drive to "Everyone", and it allowed me to change it there. But when I rebooted into Ubuntu, nothing had changed that I could see.

---

### Post by Keith_Helms on 2016-09-13
Try following the instructions in this article:
[https://wjwoodrow.wordpress.com/2014/07/23/running-minidlna-on-ubuntu/](https://wjwoodrow.wordpress.com/2014/07/23/running-minidlna-on-ubuntu/)

---

