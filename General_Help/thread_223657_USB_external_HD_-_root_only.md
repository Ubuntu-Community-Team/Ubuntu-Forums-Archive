---
title: "USB external HD - root only?"
date: 2006-07-26
forum: General Help
---

### Post by termite on 2006-07-26
I have an external USB HD.  When I plug it in, it does not automount.  When I mount it from the command line (with mount -t ntfs /dev/sda1 /media/sda1), it does not give me permission to access /media/sda1.  If I am root, I have access to it.

Problem is, I have my music stored on said HD and would like to use Rhythmbox with it.

Any ideas how I can get the mount to be readable by all rather than just root?

---

### Post by hanzomon4 on 2006-07-26
What type of filesystem does it have fat32(vfat) ntfs..?

---

### Post by Cath0de on 2006-07-26
Can't you just change the ownership on the file system of the HD?

```
chown *USERNAME* /media/sda1
```

---

### Post by aysiu on 2006-07-26
If you're manually mounting it, use this command: ```
mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222
``` If you want it to mount properly (who knows why it isn't already) by itself, do this: ```
sudo umount /dev/sda1
sudo nano -B /etc/fstab
``` Add this line to the end of that file: ```
/dev/sda1 /media/sda1 ntfs nls=utf8,umask=0222 0 0
``` Save (Control-X, Y, Enter). Then ```
sudo mount -a
```

---

### Post by termite on 2006-07-27
what exactly does umask do?

---

### Post by aysiu on 2006-07-27
> **termite said:**
> what exactly does umask do?
It defines permissions.

---

### Post by jordilin on 2006-07-27
> **termite said:**
> I have an external USB HD.  When I plug it in, it does not automount.  When I mount it from the command line (with mount -t ntfs /dev/sda1 /media/sda1), it does not give me permission to access /media/sda1.  If I am root, I have access to it.

Problem is, I have my music stored on said HD and would like to use Rhythmbox with it.

Any ideas how I can get the mount to be readable by all rather than just root?

```
chown yourusername:yourgroupname /media/sda1
```
With this command you solve the problem. Everytime you plug in your external usb hdrive it will be mounted with you as the owner not root.

---

### Post by aysiu on 2006-07-27
> **jordilin said:**
> ```
chown yourusername:yourgroupname /media/sda1
```
With this command you solve the problem. Everytime you plug in your external usb hdrive it will be mounted with you as the owner not root.
I don't believe you can use *chown* for NTFS partitions.

---

### Post by jordilin on 2006-07-27
> **aysiu said:**
> I don't believe you can use *chown* for NTFS partitions.
Oops!! you are right, aysiu. :oops: I didn't notice that the poster is talking about ntfs partitions.

---

### Post by UltraMathMan on 2006-08-04
Hi, similar problem. Tried mounting my Windows NTFS partition Disks Manager lists as /dev/sda1 with ```
sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222
``` but received the folleing error ```
mount: mount point /media/sda1 does not exist

``` Any help would be appreciated. Thank you

---

### Post by aysiu on 2006-08-04
If the mount point doesn't exist, you might have to create it first. ```
sudo mkdir /media/sda1
``` and then try this again: ```
sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222
```

---

### Post by UltraMathMan on 2006-08-05
Thanks. I get the following error ```
mount: /dev/sda1 already mounted or /media/sda1 busy
mount: according to mtab, /dev/sda1 is mounted on /tmp/disks-conf-sda1
``` so I did ```
sudo umount /dev/sda1
``` and then ```
sudo mount -t ntfs /dev/sda1 /media/sda1 -o nls=utf8,umask=0222

``` and I can now access it.
Thanks again.

---

