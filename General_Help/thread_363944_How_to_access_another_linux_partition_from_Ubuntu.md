---
title: "How to access another linux partition from Ubuntu"
date: 2007-02-17
forum: General Help
---

### Post by Hoffmann on 2007-02-17
Hi:

Is it possible to access another Linux partition from my Ubuntu partition? If affirmative, How can I do that? [My Ubuntu is a ext3, and the other partition is ext2].

Thanks!

---

### Post by gradedcheese on 2007-02-17
You just mount it.  Say the other one is named /dev/hdb2, you can make a directory to mount it to and then mount it:

sudo mkdir /mnt/hd
sudo mount -t ext2 /dev/hdb2 /mnt/hd

This will mount it and allow you to access files (and write only with sudo).  If you need to know the partition's name, the easy way is to use 'gparted', you can install it:

sudo apt-get install gparted

and then run "gksudo gparted"

---

### Post by Hoffmann on 2007-02-17
It worked. Thanks a lot!
However, I would like to have the other Linux partition mounted automatically every time I boot my machine. Os that possible?

Thanks!

---

### Post by koenn on 2007-02-17
look at /etc/fstab

look at the lines already there (eg to mount / or /home ) and add on that refers to the partition you want to mount and the directory you want to mount it to.

you need sudo to make changes to fstab,
and changes will be effective after a reboot

---

### Post by gradedcheese on 2007-02-17
> 
and changes will be effective after a reboot


or you can run "sudo mount -a" to have fstab looked at and partitions mounted immediately.

---

### Post by Hoffmann on 2007-02-17
> **koenn said:**
> look at /etc/fstab

look at the lines already there (eg to mount / or /home ) and add on that refers to the partition you want to mount and the directory you want to mount it to.

you need sudo to make changes to fstab,
and changes will be effective after a reboot

I have the following on my /etc/fstab file:

> UUID=8830E9BC30E9B0FC /Windows ntfs auto,users,rw,umask=0022 0 0

and for the other Linux partition:

> /dev/sda1	/Fedora6	-t ext2 

The Windows partition is being mounted automatically. However, that is not the case for the other Linux partition. My goal is to be able to read and write on the other partition from the Ubuntu one.

Could you, please, help me to find what I am missing?

Thanks!

---

### Post by gradedcheese on 2007-02-17
the fstab format is a little confusing.  It's space-separated, ie:

file_system mount_mount type options dump pass

The space can be spaces, tabs, whatever.  You can try this:

EDIT: see koenn's post

---

### Post by koenn on 2007-02-17
try

```
/dev/sda1        /Fedora6  ext2  defaults  0 2
```

or

```
/dev/sda1        /Fedora6  ext2  rw,user  0 2
```

---

### Post by Hoffmann on 2007-02-17
> **koenn said:**
> try

```
/dev/sda1        /Fedora6  ext2  defaults  0 2
```

or

```
/dev/sda1        /Fedora6  ext2  rw,user  0 2
```

It worked.
Many thanks to all of you!

---

