---
title: "help with fstab"
date: 2008-04-29
forum: General Help
---

### Post by Sasa_Ivanovic on 2008-04-29
I'm using Hardy Heron, and here's my problem :
I have two windows partritions, which could be mounted by going to "Places->100GB Media" in gnome desktop. But i wished to make this automatic upon booting. So i changed my fstab, and the devices are mounted but i have write privileges only on one of the partritions ( the ntfs one ). while the fat one, i can't write on it...
here's my fstab file :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=d19aa4c6-ab7c-47c3-9c13-20bc60630cdc /               ext3    relatime,error
# /dev/sdb2
UUID=4e31982c-574d-481b-bb3a-bb6577dab3e2 none            swap    sw
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# my stuff
# fat one
/dev/sdb1       /media/disk     auto    rw,user,auto,exec,umask=0222
# ntfs one
/dev/sda1       /media/disk-1   auto    rw,user,auto,exec


```

can you help me out?

---

### Post by Michael.Godawski on 2008-04-29
Perhaps this will help: (it is for feisty but the application is still active I hope)

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by Sasa_Ivanovic on 2008-04-29
> **Michael.Godawski said:**
> Perhaps this will help: (it is for feisty but the application is still active I hope)

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
It might help if i had problems with the ntfs one. I'm having problems with fat one. but thanks anyway.

---

### Post by Michael.Godawski on 2008-04-29
Oh I see now. 
The problem is the umask =0222 entry.
It must be changed to 
```
umask=000
```

The complete line should be: 
```
/dev/sdb1    /media/disk vfat  iocharset=utf8,umask=000  0    0
```

---

### Post by mahousaru on 2008-04-29
> **Sasa_Ivanovic said:**
> It might help if i had problems with the ntfs one. I'm having problems with fat one. but thanks anyway.

Try adding the options

uid=USERNAME,gid=USERNAME,umask=027

Change username for your username and the file and dir rights to what ever you need.

That should set ownership and default directory and file rights to be rwx to directories and rw to files to the owner.

---

### Post by Sasa_Ivanovic on 2008-04-29
Now it works, thanks, i appreciate your help.
```

/dev/sdb1       /media/disk     auto    rw,user,auto,exec,uid=konjo,gid=konjo,umask=000
/dev/sda1       /media/disk-1   auto    rw,user,auto,exec

```
what is umask anyway?

---

### Post by mahousaru on 2008-04-29
> **Sasa_Ivanovic said:**
> Now it works, thanks, i appreciate your help.
```

/dev/sdb1       /media/disk     auto    rw,user,auto,exec,uid=konjo,gid=konjo,umask=000
/dev/sda1       /media/disk-1   auto    rw,user,auto,exec

```
what is umask anyway?

umask sets the default rights on a directory or file

Quick bit on rights... (ignore if you are familiar)

4 - r 
2 - w
1 - x

So if you want read and write that would be 4+2=6, or rwx would be 7

Now rights are generally stated like 750 which is User,Group,Other*
*Other is everyone known to the system

(The bit on umask)
Now on creation of files/dirs the umask is used to set the default rights so if u want directories to be created by default with 750 then the mask would be

777
750
Minus the bottom from the top =
027 <- The umask for directories with the rights 750

With the mount command and fat it is used slightly differently in that it sets the rights to existing files as fat doesn't have user,group,other file rights.

Hope that makes sense

---

