---
title: "mounting a partition not working"
date: 2006-11-16
forum: General Help
---

### Post by Green_Star on 2006-11-16
I am trying to mount a Ext3 partition using ***fstab***, after rebooting my Ubuntu I am not getting write permissions to that directory where I mounted that new partition. Please refer below for my ***fstab*** settings(new mount partition in bold letters). Any suggestion?

> :~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=bebce2a2-3fa2-417a-8ca7-8c63e0c456ec / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=2650E22750E1FD85 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46,ro 0 0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=100CA2340CA2152E /media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
# /dev/hdb2 -- converted during upgrade to edgy
# UUID=7274-1454 /media/hdb2 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hdb3 -- converted during upgrade to edgy
UUID=306CB6DC6CB69C52 /media/hdb3 ntfs defaults,nls=utf8,umask=007,gid=46 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=d5499f2c-35d3-4bbd-881c-e6b1ceb965c1 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**/dev/hdb2  /my_folder/30GB ext3 defaults 0 0**
:~$ 
:~$ 
:~$ ls -l /my_folder/
total 12
**drwxr-xr-x 3 root root 4096 2006-11-13 13:24 30GB**
drwxr-xr-x 2 suma suma 4096 2006-09-20 10:05 My_Scripts
drwxrwxrwt 3 suma suma 4096 2006-11-10 08:36 vmware
:~$ 


---

### Post by koenn on 2006-11-16
according to the output of ls -l, only root has write permission on my_folder.

Whay do you mount the partition in "my_folder", and not in your home directory ?

---

### Post by Green_Star on 2006-11-16
> **koenn said:**
> according to the output of ls -l, only root has write permission on my_folder.

Whay do you mount the partition in "my_folder", and not in your home directory ?

Because I want that folder to be accessible to all the users in my machine. And I want to move my VMware images to that folder to free up some space from "/" root file system and that VMware images should accessible to all users.

So how can i resolve this issue?

---

### Post by taurus on 2006-11-16
First, change your /etc/fstab from 

```
/dev/hdb2 /my_folder/30GB ext3 defaults 0 0
```
to 

```
/dev/hdb2 /my_folder/30GB ext3 defaults 0 2
```
Then, change the permissions of /my_folder/30GB with

```
sudo chmod -R 777 /my_folder/30GB
```

---

### Post by Green_Star on 2006-11-16
Great taurus, it worked. Thanks for your help.

---

