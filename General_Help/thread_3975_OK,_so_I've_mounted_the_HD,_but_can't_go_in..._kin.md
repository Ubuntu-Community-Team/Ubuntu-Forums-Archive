---
title: "OK, so I've mounted the HD, but can't go in... kind of..."
date: 2004-11-10
forum: General Help
---

### Post by littlegreenman on 2004-11-10
Ok, so the HD is mounted. I can access it if I run the Root Terminal.

But I cannot access it using Nautilus cause I have no permission. The only way I can access it is if in a Terminal I run

sudo nautilus

and then I have root permission to access driveC.  It does not allow me to change the permissions even when root.... so altought Ubuntu gets a nice little drive icon on the desktop when I mount the HD, I cannot access it...

How do I give permission to anyone to at least access....

BTW the HD is formatted in NTFS or something... the windows format. I realise now this matters...

thanks for your help, as always :-)

diogo

---

### Post by littlegreenman on 2004-11-10
I thought I would maybe add my /etc/fstab file so you take a look... 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/driveC ntfs 
noauto,users,exec,ro,umask=000,uid=warty 0 0
/dev/hdb2 /media/driveD vfat
noauto,users,exec,umask=000,uid=warty 0 0


Drive C is a standalone drive, but driveD is just a partition of my second drive.

---

### Post by DyDx on 2004-11-10
I have the same problem...

---

### Post by ispmike on 2004-11-10
Maybe because you have "noauto" enabled? That might be a start. Here's mine, I have no problems accessing C and D.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                 /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc         /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd         /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0          /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/windows_c ntfs     ro,dmask=0222,fmask=0333   0 0
/dev/hda5       /mnt/windows_d ntfs     ro,dmask=0222,fmask=0333   0 0

---

### Post by conchobar on 2004-11-10
I had the same problem but managed to get it working after trying a lot of things in fstab. Here is the line I ended up with pertaining to my NTFS drive:

/dev/hdc1       /mnt/ntfs_disk1 ntfs    users,suid,ro,umask=2,exec,auto     0       0

The main problem with yours, I believe, is that "user" or "users" must come first, because it sets certain defaults, so having it in the middle or at the end would cancel out prior options like "exec".

Also, I think (not quite sure) that setting umask=0 will allow write access, which is kind of risky on NTFS partitions. I set it to 2 just to be safe, since I have enough room on my ext3 and vfat partitions that I wouldn't need to write to the NTFS partition, anyway.

---

### Post by littlegreenman on 2004-11-12
SOLVED!

Thank's people. 

/dev/hda1 	/media/driveC	ntfs	user,exec,ro,umask=022,uid=diogo 0 0
/dev/hdb2 	/media/driveD	vfat	user,exec,umask=000,uid=diogo 0 0


This is how it shoudl be, also, I had each of the mounts broken up into separate lines, so it wouldn't work as well...

thanks for your help
diogo

---

