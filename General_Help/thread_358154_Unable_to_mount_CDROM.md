---
title: "Unable to mount CDROM"
date: 2007-02-10
forum: General Help
---

### Post by Inhumane on 2007-02-10
When I try to insert a cd into the computer, nothing pops up in the desktop, and when I try to acess it through the computer it says : > error: could not open fstab-type file: permission denied
But when I use ```
sudo umount -t iso9660 /dev/hda  /media/cdrom0

``` it mounts. 

My fstab is as follows:
```
 # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

```

> ls -l /dev | grep cdrom output:
```
lrwxrwxrwx 1 root root           3 2007-02-10 14:00 cdrom -> hda
brw-rw---- 1 root cdrom     3,   0 2007-02-10 13:59 hda
```

---

### Post by dagnabit dang doohickey on 2007-02-10
Try changing 'noauto' to 'auto'.

---

### Post by Inhumane on 2007-02-10
> **dagnabit dang doohickey said:**
> Try changing 'noauto' to 'auto'.

No go :(
It seems like I simply don't have permissions to mount/unmount it for some reaosn, I just restarted my PC with the cd inside and it shows up on the desktop. But I can't unmount it now, > Error: could not open fstab-type file: Permission denied
eject: unmount of `/media/cdrom0' failed
 How come? This is my computer and I'm under the "root" group, I also tried setting myself to "admin". My user has everything checked under user privilages

---

### Post by dagnabit dang doohickey on 2007-02-10
Assuming you're using Gnome, take a look at the "Removeable Drives and Media Preferences" Control Panel settings.

---

### Post by Inhumane on 2007-02-10
> **dagnabit dang doohickey said:**
> Assuming you're using Gnome, take a look at the "Removeable Drives and Media Preferences" Control Panel settings.

Nothing there that would help

---

### Post by sdide on 2007-02-10
What is the attributes on the /etc/fstab?

eg. ls -l /etc/fstab

---

### Post by Inhumane on 2007-02-10
> **sdide said:**
> What is the attributes on the /etc/fstab?

eg. ls -l /etc/fstab

-rw------- 1 root root 263 2007-02-10 15:18 /etc/fstab

---

### Post by Inhumane on 2007-02-10
OK I have something that might help. It is not a pointing issue, it is indeed a permission issue.

I just logged in as another user and everthing mounts just fine.
What can I do to allow mounting (and everything else) on my own user?

---

### Post by sdide on 2007-02-10
When I do a 
```
$ ls -l /etc/fstab
-rw-r--r-- 1 root root 1211 2007-02-09 10:35 /etc/fstab
$ 
```

I suggest you do a (as root or with sudo)
```
$ chmod 644 /etc/fstab
```

and try again.

---

### Post by inception on 2007-04-01
> **sdide said:**
> When I do a 
```
$ ls -l /etc/fstab
-rw-r--r-- 1 root root 1211 2007-02-09 10:35 /etc/fstab
$ 
```

I suggest you do a (as root or with sudo)
```
$ chmod 644 /etc/fstab
```

and try again.

That seemed to have solved my problem, which displayed a similar error message. Thank you!

---

