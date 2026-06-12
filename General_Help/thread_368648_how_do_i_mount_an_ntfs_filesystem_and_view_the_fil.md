---
title: "how do i mount an ntfs filesystem and view the files?"
date: 2007-02-23
forum: General Help
---

### Post by hacc on 2007-02-23
how do i mount an ntfs filesystem and view the files?
please help me

hacc

---

### Post by kelbizzle on 2007-02-23
your ntfs filesystem... Is it a partition? or a second drive added as a slave?

---

### Post by hacc on 2007-02-23
it's a windows partition and im wondering how to access it in ubuntu

---

### Post by taurus on 2007-02-23
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by kelbizzle on 2007-02-23
ok then this is what you do. 
```
sudo fdisk -l
```
To find out where the ntfs volume is located.  Under the system column you'll see it says ntfs.
The device location will look something like this. "/dev/hda1"

If you want to mount that partiton once in a while, whenever you need it. Do this.. In terminal
**to mount the partition**
```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```

**To unmount it **
```
sudo umount /media/windows/

```

**If you want to mount it automatically at boot...do this **
```
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

Add this line to the end of your fstab
```
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0
```

and then finally remount your fstab
```
sudo mount -a
```

---

### Post by hacc on 2007-02-23
it says sudo: mount-a: command not found

---

### Post by kelbizzle on 2007-02-23
no biggie 
```
sudo mount -a
```

I forgot the space. Just copy and past this. Sorry again

---

### Post by hacc on 2007-02-23
ok that one worked but it says according to mtab, /dev/hda1 is mounted on mnt/windows.
could you IM (if you have an IM) me its hacc09 @msn, yahoo, or aol

---

### Post by kelbizzle on 2007-02-23
yea no problem.

---

