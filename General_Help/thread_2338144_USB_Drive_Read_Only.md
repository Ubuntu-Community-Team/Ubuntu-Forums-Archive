---
title: "USB Drive Read Only"
date: 2016-09-25
forum: General Help
---

### Post by Quarkrad on 2016-09-25
Running 16.04.   For some reason all my usb sticks are read only.  The attached windows pops up when I put a stick in but as you can see the options re what to do are greyed out - I'm assuming when I click OK, and there is no app set, because it is greyed out, the device is read only.  I've reconfigured the stick as fat32 via gparted.

---

### Post by sudodus on 2016-09-25
It should work automatically, but may fail in some version and flavour of Ubuntu.

You can do it manually according to these command line steps (and you can put them into a batch file to do it with one single command).

-o-

Mount a FAT32 partition in a pendrive with read/write permissions for everybody:

(assumption: the pendrive is seen as /dev/sdx, replace x with the actual drive
letter, for example b: /dev/sdx1 ---> /dev/sdb1)

```
sudo mkdir -p /mnt/sd1  # only if you want a new mountpoint
sudo umount /dev/sdx1   # only if already mounted (but with bad permissions)

sudo mount -o rw,users,umask=000 /dev/sdx1 /mnt/sd1  # mount

echo 'Hello World' > /mnt/sd1/hello.txt  # test writing
cat /mnt/sd1/hello.txt                   # test reading
```

---

### Post by Quarkrad on 2016-09-25
My pen drive is seen as sdh1 - I get:-

```
dad@dadubuntu:~$ sudo umount /dev/sdh1
[sudo] password for dad: 
dad@dadubuntu:~$ sudo mount -o rw,users,umask=000 /dev/sdh1 /mnt/sdh1  # mount
mount: mount point /mnt/sdh1 does not exist
dad@dadubuntu:~$ sudo mkdir -p /mnt/sdh1
dad@dadubuntu:~$ sudo umount /dev/sdh1
umount: /dev/sdh1: not mounted
dad@dadubuntu:~$ sudo mount -o rw,users,umask=000 /dev/sdh1 /mnt/sd1  # mount
mount: mount point /mnt/sd1 does not exist
dad@dadubuntu:~$
```

---

### Post by sudodus on 2016-09-25
You must create the mount point before you try to mount a device onto it. Try either

```
sudo mkdir -p /mnt/sdh1
sudo mount -o rw,users,umask=000 /dev/sdh1 /mnt/sdh1  # mount
```

or

```
sudo mkdir -p /mnt/sd1
sudo mount -o rw,users,umask=000 /dev/sdh1 /mnt/sd1  # mount
```

or use a different name for the mount point directory, for example **p1**, which might be easier to see.

```
sudo mkdir -p /mnt/p1
sudo mount -o rw,users,umask=000 /dev/sdh1 /mnt/p1  # mount
```

It is important that you use exactly the same name, when you try to mount, as when you created the mountpoint.

---

