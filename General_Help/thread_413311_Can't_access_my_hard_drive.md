---
title: "Can't access my hard drive"
date: 2007-04-19
forum: General Help
---

### Post by Amilius on 2007-04-19
hey, I'm using Kubuntu. I can't access my hard drive.  it's Icon is on the desktop but once I click on it I get this message:

Could not mount device

The report error was:

mount: only root can mount /dev/sda1 on /media/sda1

I'm new to the whole outside-of-windows systems, could someone please tell me how do I mount the device?

thanks

---

### Post by zvacet on 2007-04-19
You say that you** use** Kubuntu,so I think you want to access windows partition.If I´m right then
[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

---

### Post by dcstar on 2007-04-19
> **Amilius said:**
> hey, I'm using Kubuntu. I can't access my hard drive.  it's Icon is on the desktop but once I click on it I get this message:

Could not mount device

The report error was:

mount: only root can mount /dev/sda1 on /media/sda1

I'm new to the whole outside-of-windows systems, could someone please tell me how do I mount the device?

thanks

How many drives do you have?

Post the contents of your /etc/fstab file.

---

### Post by spankymasterc on 2007-04-19
use sudo command before mount 


Command :

sudo {command}

changin command to what ever u want to do no brackets

---

### Post by Amilius on 2007-04-19
sorry that I wasn't very specific.  it's an external USB hard drive.  this is the second time I install kubuntu.  the first time I did I could access the HD without problems, and it was located on the /media/ directory.  probably I messed it up when I was meddling with the manual partition options. 

btw, this is the content of my fstab file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Amilius on 2007-04-19
ok! done, I mounted it using sudo mount /dev/sda1 and it did it!!

thanks a lot!

---

