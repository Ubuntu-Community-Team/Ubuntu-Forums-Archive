---
title: "How do I?"
date: 2006-11-02
forum: General Help
---

### Post by ndemahy on 2006-11-02
Store some files on a remvoable drive that I have, it shows up in System=>>administration==>>disks, but I can' do anything with it.

I want to get some files over onto that drive so i can take them with me.

---

### Post by hexion on 2006-11-02
If it's a USB drive, just plug it and it should appear a window in your desktop with that drive.

If that doesn't work, try mounting it manually.

Removable USB disks (like pendrives) are usually in /dev/sda or /dev/sdb.... and if they have partitions you need to specify which to mount. In example, /dev/sda1 would be the first one.

To make that type

> mkdir mydisc
sudo mount /dev/sda1 mydisc
nautilus mydisc(supposing that's the correct mount point)


P.S. : Next time you open a post, try with a more usefull title ;)

---

### Post by Polygon on 2006-11-02
to figure out the /dev/whatever path i usually go into system -> admin > disks if you cant figure it out, and then just select the drive and go to partitons and its usually labeled there

---

### Post by ndemahy on 2006-11-03
sorry about the thread title, but thanks for the input

this is the error that get when trying to mount the drive

ra@Amun:~$ sudo mount /dev/sda1 mydisc
Password:
mount: you must specify the filesystem type

---

### Post by ~LoKe on 2006-11-03
> **ndemahy said:**
> sorry about the thread title, but thanks for the input

this is the error that get when trying to mount the drive

ra@Amun:~$ sudo mount /dev/sda1 mydisc
Password:
mount: you must specify the filesystem type

You have to mention the filesystem type, like...

```
sudo mount -t ext3 /dev/sda1 mydisc
```

---

### Post by ndemahy on 2006-11-04
I can't get it to work, every switch I try gives me an error.

I just want to mount the drive to the mydisc directory so I can xfer some stuff to it and take it somewhere else, any ideas?

---

