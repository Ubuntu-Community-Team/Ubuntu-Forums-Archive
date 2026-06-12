---
title: "Can't get read/write access to FAT32 partition"
date: 2007-05-14
forum: General Help
---

### Post by tiggs_the_cat on 2007-05-14
Hello,

I was installing Ubuntu Feisty the other day for the very first time and everything seemed to work fine up to the point where I formatted a partition under Windows from NTFS to FAT32 in order to be able to write to it from Linux. 

Now it seems I can still read files on it but there seems to be no way I can write to it. I've been trying to use the File Browser with sudo nautilus but I still only get the error message that I don't have the permission to change the access rights. I also tried changing the permissions from the terminal as was said in another thread but with no luck.

I am getting desperate, please help!

---

### Post by cotcot on 2007-05-14
Have you check [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_us")?

---

### Post by tiggs_the_cat on 2007-05-15
Hey again,

Okay, I did what somebody suggested in another thread and did

Here is the result:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=56bb2aeb-723d-4e05-8e1b-11b095eccd4f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=B61C56591C561529 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=4EC8D8F0C8D8D775 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=2008DB8D08DB5FF8 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=B85CDF405CDEF858 /media/sda8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=970b2a2c-dd0b-4540-841f-23fa3a0e78ac none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

So I assume sda8 is supposedly NTFS? Both Windows and also GParted under Linux know that it is FAT32 (see attachment). How can I change it to be mounted as FAT32?

Also thank you for the link to the documentation!

:)

---

### Post by cotcot on 2007-05-15
Supposing it is /sda8 you changed.
Modify in fstab (sudo gedit /etc/fstab) :

```
# /dev/sda8
UUID=B85CDF405CDEF858 /media/sda8     [COLOR="Blue"]ntfs    defaults,nls=utf8,umask=007,gid=46 0       1[/COLOR]
```
to
```
UUID=B85CDF405CDEF858 /media/sda8    [COLOR="Red"] vfat  iocharset=utf8,umask=000  0    0[/COLOR]
```

This is explained in item 1.17.4 of the link in my previous post.

---

### Post by tiggs_the_cat on 2007-05-15
Hey,

Thank you very much for the fast help, that did the job! :popcorn:

Well, I was thinking a search on Google and he forums here would be a good start, and it appears there are many people that have problems mounting FAT32 partitions with read/write access and none of those suggestions seemed to help so far.

Best regards,

---

