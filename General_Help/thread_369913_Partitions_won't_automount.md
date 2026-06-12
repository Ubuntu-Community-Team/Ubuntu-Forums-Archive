---
title: "Partitions won't automount"
date: 2007-02-25
forum: General Help
---

### Post by Iskendar on 2007-02-25
Hi all,

 I have some problems with mounting partitions. This is a copy of /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hdd1
UUID=3c70bdda-a73f-454c-9a26-1ba6ef6e2306 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda2
UUID=c00f459e-fd54-4602-b5c7-98d4272a16a0 /boot ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda1
UUID=F2E83150E83113F7 /media/hda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/hda5
UUID=e6e1d876-dc55-4665-a81a-d4fb54a9e1bc /media/hda5 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda7
UUID=1f595962-ccb6-47f9-bbf2-46fcb62ab69c /media/hda7 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hdd2
UUID=f81f614b-3df3-4bc1-8ffa-ccb02e4ac799 /home/ab/hdd2 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hdd3
UUID=8b5799b8-5bca-44d1-8ee5-18aa976c3f3c /home/ab/hdd3 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hdd4
UUID=7f1c6c4e-1160-464f-886a-4ac6c0fd6325 /home/ab/hdd4 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda6
UUID=1feef07d-c0bc-49ac-94c2-c941d248e504 /home reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda3
UUID=3bfbd205-be82-417c-afd3-394361268f0f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0

```

Basically, hdd1 is /,  hda2 is /boot,  hda3 swap and hda6 is /home. These get mounted at boot time just fine. Of the others, hda1 is windows, hda5 and hda7 my old gentoo install, and hdd2, hdd3 and hdd4 data partitions, don't get mounted unless I do so manually. Now, I see no difference in options between hda6 and hdd3, so I wonder why the first gets mounted at boot time, and the other doesn't. Don't get it really. Any help?

---

### Post by temba on 2007-02-25
Hi there,

did you edit the fstab file yourself or did Ubuntu do it for you?

Either way, make sure that the folders are created in the media folder.

are you sure that hddx is not supposed to be hdbx?

Another thing you can try is to comment out the UUID and manually type in the device eg /dev/hdd2 - I had to do this when I installed Linux Mint and wanted to use the same swap partition for both Linux Mint and Kubuntu.

---

### Post by Iskendar on 2007-02-25
> **temba said:**
> Hi there,

did you edit the fstab file yourself or did Ubuntu do it for you?

Did it myself, originally the entries pointed towards /media/hddx

> **temba said:**
> 
Either way, make sure that the folders are created in the media folder.

So the fstab entries have to point to /media/something? It's not possible to mount devices anywhere else? Why? It was no problem in my old gentoo install. Something to do with hald?

> **temba said:**
> 
are you sure that hddx is not supposed to be hdbx?


Nope. First disk is hda, optical drive hdc and second disk hdd. I can mount manually just fine, by the way.

> **temba said:**
> 
Another thing you can try is to comment out the UUID and manually type in the device eg /dev/hdd2 - I had to do this when I installed Linux Mint and wanted to use the same swap partition for both Linux Mint and Kubuntu.

Ok, I'll try it. Can't reboot now, so I'll comment on that later.

---

### Post by Iskendar on 2007-02-25
> **Iskendar said:**
> 

Ok, I'll try it. Can't reboot now, so I'll comment on that later.

Ok, so I replaced the UUID entry for one of them with /dev/hdd4 in /etc/fstab:

```
/dev/hdd4 /home/ab/hdd4 reiserfs nouser,defaults,atime,auto,rw,dev,exe
c,suid 0 2

```

After a reboot, same situation. /home/ab/hdd4 is empty, I have to sudo mount it manually. Weird, goes against all I thought to know about the fstab system.

---

### Post by Iskendar on 2007-02-27
Bump

Come on guys, any help on this? Why is this not working, it should be trivial fstab functionality, shouldn't it?
What's preventing these partitions from mounting at boot time? Some sort of conflict with hald maybe?

---

### Post by Iskendar on 2007-03-05
Bump

Anyone?

---

### Post by Iskendar on 2007-03-07
Ok, got the answer [here]("http://www.linuxquestions.org/questions/showthread.php?t=533357"). Apparently, it's an order issue. The partitions which didn't get mounted were listed in /etc/fstab befor the 
/home partition, meaining they failed to mount because the directory didn't exist yet.

---

