---
title: "Partition Permissions"
date: 2007-06-17
forum: General Help
---

### Post by Abbobo on 2007-06-17
Hello,
I am having trouble getting my new hard disk to work properly. Its 500gb fat32.
Root is the owner of the partition so I cannot write to the disk. I have tried using sudo chown -R abi /media/sdb1 but it just says 'Operation not permitted' next to each file. 
I have tried opening nautilus as root and changing the permissions in properties, but to no avail.
I have tried unmounting the disk, changing the permission on the dev file, and remounting. I cannot get this to work.

Does anyone know how I can fix this?
Thanks
abi

---

### Post by smoker on 2007-06-17
> **Abbobo said:**
>  I have tried using sudo chown -R abi /media/sdb1 but it just says 'Operation not permitted' 
Does anyone know how I can fix this?
Thanks
abi

hi, try: > sudo chown -R abi:abi /media/sdb1 

best of luck

---

### Post by Abbobo on 2007-06-17
Thanks for the suggestion, but it give the same result; 'Operation not permitted'

:(

---

### Post by smoker on 2007-06-17
try following this then:
> sudo chown -R abi:abi /media/sdb1
then
> chmod -R 777 /media/sdb1

i'm no expert at this, so hope it works, or someone can give more info:-)

---

### Post by qpieus on 2007-06-17
Please post the contents of your /etc/fstab file.

---

### Post by Abbobo on 2007-06-17
chmod -R 777 /media/sdb1 returns the same as the others.

My fstab file contains:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2fe6e076-a19c-470b-85f2-df852f5c2e98 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9260180F6017F8A5 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=466D-967C  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=a58742d0-4268-4c09-b480-20443a7487be none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I am having troubles with a few other things too, due to using the amd64 architechture. I am going to give in and install the 32bit version. Hopefully I won't have this problem once thats done. If i do, I will renew the thread.

Thanks for your help guys.
abi

---

### Post by qpieus on 2007-06-17
If you still have troubles later be sure to post. Here are some references on mounting fat32 drives:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

[http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,NTFS](http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,NTFS))

From the gentoo page, there's a section on mount options, which is actually from the man page. In there it talks about the *user* option that allows regular users to read/write. That may be what you need.

>  user, users: let users mount and unmount

Taking a page from man mount (which explains it much better than we ever could),

"Normally, only the superuser can mount file systems. However, when fstab contains the user option on a line, then anybody can mount the corresponding system.

Thus, given a line in /etc/fstab

 /dev/cdrom  /mnt/cdrom  iso9660  ro,user,noauto,unhide


the umask=000 option from the psychcats page does about the same thing. I have my fat32 partition mounted with that option and it works.

---

### Post by louistan3 on 2007-06-28
i dont think you're supposed to have defaults on a vfat in fstab.. 

i had the same problem with my vfat hard drive not mounting and i took out defaults and it mounted...

```
iocharset=utf8,umask=000 0 0
```

i have those as my options... 

but im not an expert.. :P

---

### Post by bodhi.zazen on 2007-06-28
+1 louistan3 \0/

fat and ntfs permissions are set at the time of mount.

So options with mount or in fstab :

uid=<user>,gid=<group>,umask=007

uid = user
gid = group
umask = permissions

So ...

mount /dev/hdxy /media/data -o uid=1000,gid=100,umask=007

fstab
/dev/hdxy /media/data vfat uid=bodhi,gid=users,umask=007 0 0

*You can use the user name or number, group name or number, dealer's choice

---

