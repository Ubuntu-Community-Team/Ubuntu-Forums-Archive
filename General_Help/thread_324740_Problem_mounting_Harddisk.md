---
title: "Problem mounting Harddisk"
date: 2006-12-24
forum: General Help
---

### Post by oink on 2006-12-24
Hi everbody,

Iam running a Ubuntu server setup as my Email, web an file server. Now i've added some disk to to store photo's and make backups of my photo's and mail, but i can't mount the extra drives.

This is the contents of my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /docs		ext3    defaults        0       2
/dev/hda2       /boot           ext3    defaults        0       2
/dev/hdc1       /dataserver     ext3    defaults        0       2
/dev/hdd1       /backup	        ext3    defaults        0       2
/dev/hda4       /var            ext3    defaults        0       2
/dev/hda1       none            swap    sw              0      2

but the added hdb(1) and hdd(1) are not mounted. They are present in /dev/ and if if i run fdisk -l i see they are present, but when i try to mount them manually i get this response:

mount: /dev/hdb1 already mounted or /docs busy
mount: /dev/hdd1 already mounted or /backup busy

They are not mounted so they must be busy. I already googled and searched the forum for this and i already removed "evms" but this doesn't help.

I'am really out of ideas can someone help me!!

Many thanks in advance,
greeting Matthijs

---

### Post by bodhi.zazen on 2006-12-24
Not to ask the obvious, but have you made the mount points?

```
sudo mkdir /docs
sudo mkdir /backup
sudo mount -a
```

also, why not use a more "traditional" mount point like /mnt/docs or /media/backup ?

---

### Post by oink on 2006-12-24
Thanks for the fast reply,

Yes, i've created the mounting points.
And if everything works i will think about the location of the mounting point.

But i think some process is keeping the mounting point busy and that's why i can't mount the drives. Or i'am forgetting something crucial.

---

### Post by bodhi.zazen on 2006-12-24
I am not seeing anything obvious.

Does rebooting or moving to a more traditional mount point help ?

---

### Post by oink on 2006-12-24
I directly tried that when you mentioned it, and it makes no difference.
I have found a strange thing while rebooting.
Ubuntu checks the filesystems while booting and there it stil gives the "old" names (/backup and /docs) instead of the "new" names (/mnt/docs and /mnt/backup). 
Do you know what controls thing filesystem check?

Gr Matthijs

---

### Post by bodhi.zazen on 2006-12-24
fstab

Last number = check on mount

0 = no
1= check first, use for root patition
2 = check after root, numbers > 2 are, to my knowledge, not used ....

You need to update fstab to your new mount points .....

? reboot

---

### Post by oink on 2006-12-24
Something very strange is going on here.
With info from [http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)
I placed forcefsck in root so a filesystem check is forced on reboot.
And while my fstab looks like this
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /mnt/docs  ext3    defaults        0       2
/dev/hda2       /boot         ext3    defaults        0       2
/dev/hdc1       /dataserver     ext3    defaults        0       2
/dev/hdd1       /mnt/backup     ext3    defaults        0       2
/dev/hda4       /var            ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0


```

Ubuntu starts to check /backup and /docs!! And /docs takes quite some time because i have a lot of document from an earlier setup on that disk.

It looks like the information in fstab is ignored by this filesystem check, but i really don't have any idea where i should look.

Gr Matthijs

---

### Post by oink on 2006-12-24
Ok, the name that is given during the filesystem check is just a name you can change with
```
sudo tune2fs -L name /dev/<devicename>

```
So i'am back where i started. I really dont get it, mounting a disk can't be this hard!! 
I did it numerrous times in 5.10 and now in 6.06 it's a problem?

---

### Post by bodhi.zazen on 2006-12-24
Your problem is most odd.

Have you set any customized boot scripts ?

---

### Post by oink on 2006-12-24
No, i didn't change anything in the boot setup except fstab.
I did find one strange thing. Look at the four next outputs.
```
root@Server06:/home/matthijs# ls -l /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root  9 2006-12-24 18:14 ata-IC35L040AVER07-0_SXTTXLY9623 -> ../../hda
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 ata-IC35L040AVER07-0_SXTTXLY9623-part1 -> ../../hda1
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 ata-IC35L040AVER07-0_SXTTXLY9623-part2 -> ../../hda2
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 ata-IC35L040AVER07-0_SXTTXLY9623-part3 -> ../../hda3
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 ata-IC35L040AVER07-0_SXTTXLY9623-part4 -> ../../hda4
lrwxrwxrwx 1 root root  9 2006-12-24 18:14 ata-IC35L080AVVA07-0_VNC403A4GUUPUG -> ../../hdc
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 ata-IC35L080AVVA07-0_VNC403A4GUUPUG-part1 -> ../../hdc1
lrwxrwxrwx 1 root root  9 2006-12-24 18:14 ata-SAMSUNG_SV2042H_0273J1FR820846 -> ../../hdd
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 ata-SAMSUNG_SV2042H_0273J1FR820846-part1 -> ../../hdd1
lrwxrwxrwx 1 root root  9 2006-12-24 18:14 ata-SAMSUNG_SV2042H_0347J1ER802969 -> ../../hdb
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 ata-SAMSUNG_SV2042H_0347J1ER802969-part1 -> ../../hdb1

```
```
root@Server06:/home/matthijs# ls -l /dev/disk/by-path/
total 0
lrwxrwxrwx 1 root root  9 2006-12-24 18:14 pci-0000:00:11.1-ide-0:0 -> ../../hda
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 pci-0000:00:11.1-ide-0:0-part1 -> ../../hda1
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 pci-0000:00:11.1-ide-0:0-part2 -> ../../hda2
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 pci-0000:00:11.1-ide-0:0-part3 -> ../../hda3
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 pci-0000:00:11.1-ide-0:0-part4 -> ../../hda4
lrwxrwxrwx 1 root root  9 2006-12-24 18:14 pci-0000:00:11.1-ide-0:1 -> ../../hdb
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 pci-0000:00:11.1-ide-0:1-part1 -> ../../hdb1
lrwxrwxrwx 1 root root  9 2006-12-24 18:14 pci-0000:00:11.1-ide-1:0 -> ../../hdc
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 pci-0000:00:11.1-ide-1:0-part1 -> ../../hdc1
lrwxrwxrwx 1 root root  9 2006-12-24 18:14 pci-0000:00:11.1-ide-1:1 -> ../../hdd
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 pci-0000:00:11.1-ide-1:1-part1 -> ../../hdd1

```
so far everything is alright. But then
```
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 4b769fc8-db69-4bf6-bb1e-f90da711b6b0 -> ../../hdc1
lrwxrwxrwx 1 root root  9 2006-12-24 18:14 7a6f39fb-ca66-4e1d-8e99-145c6224ed91 -> ../../md0
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 bd5b032a-d252-4400-8d9c-b2b46e4c6e45 -> ../../hda3
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 cc954a45-cff1-8328-8c16-a4482c718b05 -> ../../hdd1
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 ea5df4f1-aed1-4d5a-8e2d-08fc9db1f18a -> ../../hda2
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 ec011f4f-975a-4dc6-b243-1f04f8540e16 -> ../../hda4

```
There is no hdb1 and hdd1 but only one md0 (raid device). There is a raid controller on the mainboard but its not connected and disabled in the BIOS.

```
root@Server06:/home/matthijs# ls -l /dev/disk/by-label/
total 0
lrwxrwxrwx 1 root root  9 2006-12-24 18:14 devhdb1 -> ../../md0
lrwxrwxrwx 1 root root 10 2006-12-24 18:14 server -> ../../hdc1

```
And here is md0 again.

I have used the raid controller in the past with this setup but later on i just used the two basic IDE controllers.

Looks like the ubuntu doesn't update the disk configuration. Can i do this manually??

---

### Post by oink on 2006-12-24
Yes!!! 
I almost cracked it.
```

mdadm --manage --stop /dev/md0
mdadm --manage --remove /dev/md0
mount -a

```
This stops the partition and remount my disks.
Only the remove option is overruled by a startup script.

Does anyone have a idea which scripts it is?

---

### Post by oink on 2006-12-25
Right now i've placed the commands in my last post in the pc.local.
This work fine but isn't a very "clean" solution i think.

bodhi.zazen, thanks for your help sofar!!!

---

### Post by psusi on 2006-12-27
The partitions appear to be configured as a software raid.  You need to destroy the raid ( not just stop it ).  Also what is the partition type according to fdisk?  I hope it is not set to raid auto detect.

---

