---
title: "Unable to to write to drive."
date: 2007-10-17
forum: General Help
---

### Post by maikie on 2007-10-17
I have one drive which i wish to use on ubuntu.
It was originally NTFS, but i deleted that partition and created an ext2 partition.

But, now i dont have write permissions to that drive.
I believe i have to make change to /etc/fstab but unsure on those changes.

---

### Post by LanDan on 2007-10-17
# <file system>     <mount point>   <type>  <options>   <dump >  <pass>
/dev/hdaX            /folderwhereyouwantit            ext2    defaults    0       2

should be something like this in fstab i think where X is your drive number (hda could also be something like sda)
use the command df to see your drives

---

### Post by bodhi.zazen on 2007-10-17
> **maikie said:**
> I have one drive which i wish to use on ubuntu.
It was originally NTFS, but i deleted that partition and created an ext2 partition.

But, now i dont have write permissions to that drive.
I believe i have to make change to /etc/fstab but unsure on those changes.

No, fstab is fine ...

```
sudo mount /dev/partiton

sudo chown -r root.users /mount/point

sudo chmod -r 770 /mount/point
```

---

### Post by alb@nian on 2007-10-19
How can I do it with a ex3 partition???

---

### Post by alb@nian on 2007-10-19
I want to enable writing in one of my partions.

```
sudo mount /dev/partiton
```

This command do not work because my partition is already mounted.
Any advice, I'm a begginer and I don't understand very well all the commands.

---

### Post by alb@nian on 2007-10-19
This are in the fstab file

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=14f9fbc2-a86b-4914-92e9-1d8f940afb5b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=BE647D37647CF38D /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=FA22197A22193D57 /media/sda4     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=adfe4010-4f5e-44b8-ad7c-83c567137fae /media/sda5     ext3    rw        0       2
# /dev/sda6
UUID=0ec87718-8b70-4df5-90c5-62d8aae9faab none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by bodhi.zazen on 2007-10-19
> **alb@nian said:**
> I want to enable writing in one of my partions.

```
sudo mount /dev/partiton
```

This command do not work because my partition is already mounted.
Any advice, I'm a begginer and I don't understand very well all the commands.

Where is it mounted ?

```
mount
```

Which partition in fstab ??

I assume /media/sda5

So, 

```
sudo chown root.users /media/sda5
sudo chmod -r 770 /media/users
```

---

### Post by alb@nian on 2007-10-20
> **bodhi.zazen said:**
> Where is it mounted ?

```
mount
```

Which partition in fstab ??

I assume /media/sda5

So, 

```
sudo chown root.users /media/sda5
sudo chmod -r 770 /media/users
```
With what shoud I replace this sentence 

```
sudo chmod -r 770 /media/users
```

---

### Post by alb@nian on 2007-10-20
Guys thnx for your help, I found how to do it.
All I needed was this command

```
gksudo nautilus
```

I still don't understand why I can open it this way and not directly. Anyway I will continue searching and learning.



I found this at this site:

```
http://www.psychocats.net/ubuntu/permissions
```

---

