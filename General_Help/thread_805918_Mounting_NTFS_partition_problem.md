---
title: "Mounting NTFS partition problem"
date: 2008-05-24
forum: General Help
---

### Post by MEGA. on 2008-05-24
Hello,

All NTFS partition is working great except only one partition i can't mount it , i tried to add it to fstab , but every time told me unable to mount the volume /

is there any way to mount it ?

[IMG]http://img208.imageshack.us/img208/1641/screenshotpt9.png[/IMG]

this partition /

using ubuntu 8.04

thanks in advance

---

### Post by omababy on 2008-05-24
try:

sudo mount /dev/drive /mountpoint -o force

**substitute drive & mountpoint

---

### Post by realthor on 2008-05-24
or smth like:

sudo mount -t ntfs-3g /dev/sda1 /mnt/windows

also sda1 and windows are examples. use your own.

---

### Post by MEGA. on 2008-05-24
> **omababy said:**
> try:

sudo mount /dev/drive /mountpoint -o force

**substitute drive & mountpoint

i try it but this appear to me 

```
sudo mount /dev/sdb5 /media/disk2 -o force
mount: wrong fs type, bad option, bad superblock on /dev/sdb5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by MEGA. on 2008-05-24
solved guys 

i was have to enable ntfs 3g

have a nice day

---

