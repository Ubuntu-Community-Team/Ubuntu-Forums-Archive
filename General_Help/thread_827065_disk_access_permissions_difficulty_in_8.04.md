---
title: "disk access permissions difficulty in 8.04"
date: 2008-06-12
forum: General Help
---

### Post by ymp on 2008-06-12
I continually run into error messages disallowing me to move folders to or write files to vfat drives on a new install of Hardy/8.04.
fstab is below
system is dual ubuntu/winxp, and I must keep some drives in vfat
I tried changing 'defaults' to 'unmask=000' as advised in some other posts, but that made the drives unreadable
only the ntfs, win system disk is available, but I can't see what is different about it in fstab
also, what do the long strings begining with UUID=..., mean?
assistance appreciated
------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=6bf7d736-789d-4155-b64e-43198ec2c1e7 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda8
UUID=b0004614-7670-40c0-9fce-7113e698c7a0 /home ext3 relatime 0 2
# /dev/sda7
UUID=cd0d92cc-f301-4adc-b93b-06de39129a66 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda9 /media/filearc vfat defaults 0 0
/dev/sda10 /media/filearc2 vfat defaults 0 0
/dev/sda1 /media/winos ntfs defaults 0 1

-----------
:(

---

### Post by joshsmith on 2008-06-13
uuid gives linux its coded location of the drive


you want 
umask=000
not unmask

that should work for vfat and ntfs ie:
/dev/sda9 /media/filearc vfat defaults,umask=000 0 0

---

### Post by ymp on 2008-06-13
thanks for the clarification, however, this did not change my inability to write to the disk, 
it is readable, but when I try to alter and save a file, or transfer a file I receive an error message stating I do not have permissions to do so

---

### Post by drs305 on 2008-06-13
Try adding "**gid=1000**" after "defaults," to make your group the owner of the partition.

---

### Post by joshsmith on 2008-06-13
to make you the owner, you actually want
uid=1000,gid=1000
assuming you are the only user

---

### Post by ymp on 2008-06-13
I have edited fstab but this did not alter the problem, when I try to copy or save files within the directory I receive an error message stating that:
... you do not have permissions to create it in the destination.
This is really getting to be a pain, I just don't understand it,
I unmounted one of the partitions, reformatted it, and then mounted it and I still am experiencing the same inabilty to write to it, unless I run Nautalus under sudo mode.

---

### Post by drs305 on 2008-06-13
> **ymp said:**
> I have edited fstab but this did not alter the problem, when I try to copy or save files within the directory I receive an error message stating that:
... you do not have permissions to create it in the destination.
This is really getting to be a pain, I just don't understand it,
I unmounted one of the partitions, reformatted it, and then mounted it and I still am experiencing the same inabilty to write to it, unless I run Nautalus under sudo mode.

Have you tried to change the ownership of the mount point?
```
sudo chown -R username:username /media/filearc
```

---

### Post by cariboo on 2008-06-13
Have you tried:

```
/dev/sda1 /media/winos ntfs defaults,user,rw 0 1

```

in fstab.

Jim

---

### Post by ymp on 2008-06-13
problem solved
when I changed the mount point to be the same as the /dev name, and used  'auto,user,sync,exec,uid=1000,gid=1000,umask=007 0 0' permission string it resolved my write and copy problems, 
strange since I should be able to mount it to any name, anyway, that resolved the problem
thanks for the suggestions

---

