---
title: "Problem formatting with Gparted"
date: 2007-04-30
forum: General Help
---

### Post by merlinus on 2007-04-30
I was able to format a new partition as Fat32, but when I tried to do this as Ext3, Gparted returned an error message:

An error occurred while applying the operations

The following operation could not be applied to disk:

Format /dev/sda7 as ext3

The details simply repeated the error messages.

Help appreciated!

-merlin

---

### Post by taurus on 2007-04-30
You can format it to ext3 from a terminal.  No need to use gparted for that.

Applications -> Accessories -> Terminal
```
sudo mke2fs -j /dev/sda7
```

---

### Post by merlinus on 2007-04-30
I followed your directions, and when I tried to mount the partition, this error message came up:

Failed to mount volume.

Failed to determine the mount point for /dev/sda7.

Cannot mount volume.

mount: wrong fs type, bad option, bad superblock on /dev/sda7, missing codepage or other error.

Thanks...

-merlin

---

### Post by taurus on 2007-04-30
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda7   /media/sda7   ext3   defaults   0   1
```
Save the change.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sda7
sudo mount -a
df -h
```

---

### Post by merlinus on 2007-04-30
Thanks!  It shows up now in System/Adminstration/System Monitor.

Will this partition mount automatically from now on?

-merlin

---

### Post by taurus on 2007-04-30
Yip.  /dev/sda7 will be mounted to /media/sda7 every time you boot Ubuntu.  And if you want to write to it without being root (using sudo), then you can change the ownership of /media/sda7 from root to your login name.

```
sudo chown -R **username**:**username** /media/sda7
```
where **username** is your login name.

---

### Post by merlinus on 2007-04-30
Thanks again!

Another question, if I may.

If I move /home to sda7, and /root is on sda8, will grub still work correctly?  After several agonizing hours today before finding out how to fix the boot loader, I have zero desire to go there again.

-merlin

BTW, if your handle is linked with your sun sign, happy birthday!

---

