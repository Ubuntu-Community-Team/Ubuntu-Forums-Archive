---
title: "directory turned into regular file"
date: 2007-05-01
forum: General Help
---

### Post by flostre on 2007-05-01
Hello,

on my FAT32 partition a folder turned into a regular file of the same name (size 32K) for apparently no reason. I did not do anything funky with it, just moving files into it and copying it. This dates back a while now, so I really can't see any reason for the mutation. Is it possible to just "set the dirctory bit" or so? The only other strange thing is that when I tried to unmount the FAT32 partition, I get the error that the partition does not match /etc/fstab. Sorry, I don't know the exact error message, since I don't dare boot the affected system anymore out of fear, other folder might also mutate - we are talking about my digital photo archive here.

Thanks in advance,

flostre

Edit: To be a bit more specific: I have one folder for all photos from my new camera. In there, there are folder for all events/occasions where I took photos. Two of these folders turned into files, the others are fine. I cannot see what should be so special about them; one had around 20 images, the other one around 200. Last access was to another folder.
You might have guessed that I have a dual boot system from the fact that I have a FAT32 partition. So I tried booting Windows, and there it's the same problem.

---

### Post by flostre on 2007-05-02
*up*

---

### Post by haricharan on 2007-05-02
> **flostre said:**
> The only other strange thing is that when I tried to unmount the FAT32 partition, I get the error that the partition does not match /etc/fstab. Sorry, I don't know the exact error message, since I don't dare boot the affected system anymore out of fear, other folder might also mutate - we are talking about my digital photo archive here.


can you post ur contents of fstab
```
cat /etc/fstab
```

---

### Post by flostre on 2007-05-02
Okay, so did boot the affected system despite my fears and it looks like it worked out.


Here is the contents of /etc/fstab (/dev/hda2 is the partition in question):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5 -- converted during upgrade to edgy
UUID=819fc7cd-ee6e-417b-835b-ba3b540906d2 / ext3 defaults,errors=remount-ro 0 1
#/dev/hda1       /media/hda1     vfat    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=08C5-24BC /media/hda2 vfat exec,nosuid,rw,user,check=strict,uid=1000,gid=1001,auto 0 0
# /dev/hda6 -- converted during upgrade to edgy
#UUID=f4663969-8253-4fee-86f6-2de1601c41d1 -- reconverted by me
/dev/hda6       none swap sw 0 0
#/dev/hda6      none swap defaults 0 0
#UUID=57d7348f-0c17-45fd-964d-2bed5fbe6e9a      none swap sw 0 0
#/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
I am running Edgy and have done so for a while.

Here is /etc/mtab:
```
/dev/hda5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-11-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hda2 /media/hda2 vfat rw,noexec,nosuid,nodev,check=strict,uid=1000,gid=1001 0 0

```

The error I mentioned above was not really present - it was due to me trying to unmount the wrong partition. Remounting the FAT32-partition works fine but does not solve the problem.

flostre

---

### Post by haricharan on 2007-05-02
> **flostre said:**
> 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5 -- converted during upgrade to edgy
UUID=819fc7cd-ee6e-417b-835b-ba3b540906d2 / ext3 defaults,errors=remount-ro 0 1
#/dev/hda1       /media/hda1     vfat    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
** UUID=08C5-24BC /media/hda2 vfat exec,nosuid,rw,user,check=strict,uid=1000,gid=1001,auto 0 0**
# /dev/hda6 -- converted during upgrade to edgy
#UUID=f4663969-8253-4fee-86f6-2de1601c41d1 -- reconverted by me
/dev/hda6       none swap sw 0 0
#/dev/hda6      none swap defaults 0 0
#UUID=57d7348f-0c17-45fd-964d-2bed5fbe6e9a      none swap sw 0 0
#/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```I am running Edgy and have done so for a while.

Here is /etc/mtab:
```
/dev/hda5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-11-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
** /dev/hda2 /media/hda2 vfat rw,noexec,nosuid,nodev,check=strict,uid=1000,gid=1001 0 0**

```


Looks like you have messed your fstab file...the UUID is a 16 byte number [http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID) ...thats the reason it doesnt get mounted automatically..and u have to remount.... try to see if you have a backup or change the bold line in fstab with the one in mtab... and it shud work....do create a backup of ur fstab just in case if you need it later....

---

### Post by orb9220 on 2007-05-02
> UUID=08C5-24BC /media/hda2 vfat exec,nosuid,rw,user,check=strict,uid=1000,gid=1001,auto 0 0

If it is a fixed drive you do not need an uuid mine is 

# /dev/sdb1
/dev/sdb1     /home/orb/Drives/114GB-fat32/     vfat    defaults,utf8,umask=007,gid=46 0       0

and it works normally in Feisty.

Why all the

exec,nosuid,rw,user,check=strict,uid=1000,gid=1001,auto 0 0

just curious as never seen a fat32 with so many options.

Mine gives me full read and write.

Hope it helps.

---

### Post by flostre on 2007-05-03
> **haricharan said:**
> Looks like you have messed your fstab file...the UUID is a 16 byte number [http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

Well, it was converted during the upgrade to Edgy.

> thats the reason it doesnt get mounted automatically..and u have to remount
It gets automounted, I don't have to remount. I was just trying to see if it works. 

And please remember that the problem is that two folder turned into regular files for no apparent reason. I cannot see how this could be connected to a invalid /etc/fstab. Mounting does not change the contents of a directory, right? Also, the fstab-line for the vfat partition has been unchanged since my upgrade to edgy (which I did shortly after edgy was stable), and the problem occured recently for the first time.

Still thank you for your help.

PS @orb: as you can see from the comment, the line was created by the upgrade to edgy. I don't remember how many of the parameters I had added myself. I had had problems with write-access to the partition, I guess that is the reason. Since everything is working fine now, I hesitate to touch the file :D

---

### Post by flostre on 2007-05-04
Is it possible to just "set the directory bit" of a file?

flostre

---

### Post by Adramelech on 2007-05-04
Theres actually a bit to identify those files as directories but i dont know how to change it. Can you post the output of:

file MyChangedDir

?

---

### Post by flostre on 2007-05-04
```

MyChangedDir: data

```

---

### Post by flostre on 2007-05-06
Does anyone know a tool to search for lost files in fat-partitions?

---

### Post by flostre on 2007-05-09
*up*

I was asking for a really dirty hack - why is nobody interested? :)

---

### Post by flostre on 2007-05-15
Please, people, help.

:( :confused: 

(last try)

---

