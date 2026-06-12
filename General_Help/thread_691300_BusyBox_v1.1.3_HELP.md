---
title: "BusyBox v1.1.3 HELP"
date: 2008-02-08
forum: General Help
---

### Post by jonhill90 on 2008-02-08
I just used Norton Ghost to copy Ubuntu from on hard drive to another. it worked but when the ubuntu loading screen comes up it drops into busybox and i get this error:
Busybox v.1.1.3(Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)

and its waiting for a command starting with:
Initramfs

i have no idea what to do but i cannot reinstall linux. It sill works on the harddrive i ghostes from.
I cannot get past to ubuntu loading screen

---

### Post by taurus on 2008-02-08
Bet you a penny that the UUID for / partition is all wrong.  Therefore, it can't find / to boot from.

So, you need to replace the UUID in /boot/grub/menu.lst and /etc/fstab with the new one.  Otherwise, you can go back to the old fashion and use /dev/sda1 (or whatever partition / is resided on).

---

### Post by jonhill90 on 2008-02-08
how would i do that? i am pretty new to linux could you tell me what i need to do

---

### Post by taurus on 2008-02-08
Perhaps you can do that from the LiveCD.  Do you have a LiveCD handy somewhere so you can boot your machine with it?  If you do, then wait for it to boot up and post the output of this command since you need to mount your harddrive where / is and modify both /etc/fstab & /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by jonhill90 on 2008-02-08
is that all or is there more i need to do i have a live disk

---

### Post by taurus on 2008-02-08
Once I know which partition your / is on the harddrive, then we need to mount it and then we can edit those two files.

---

### Post by jonhill90 on 2008-02-08
this is what i got:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004acbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30027   241191846   83  Linux
/dev/sda2           30028       30401     3004155    f  W95 Ext'd (LBA)
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by taurus on 2008-02-08
Run

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
```
That will mount your Ubuntu partition, /dev/sda1, to /mnt/ubuntu.  Now, can you post the outputs of these two commands?

```
cat /mnt/ubuntu/etc/fstab
cat /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by rwhitt on 2008-02-08
are both hard drives still mounted in the box? ive seen the busy box screen when attempting to boot with two hard drives mounted. i succesfully booted a machine with two hard drives, however i could not see the other drive. ive ghosted hundreds of xp machines and ive attempted to ghost a few ubuntu machines unsuccessfully. when trying to boot a ghosted drive  it came up with a black screen only saying "grub"  however ive found it much easier to install Ubuntu as it doesn't take very long to install from a cd.

---

### Post by jonhill90 on 2008-02-08
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by jonhill90 on 2008-02-08
above is the error

also i only have one hard drive mounted

---

### Post by taurus on 2008-02-08
What filesystem did you use for /dev/sda1 anyway?

What happen if you just mount it?

```
sudo mount /dev/sda1 /mnt/ubuntu
```

You said you have one harddrive mounted, which one is it?

```
df -h
```

---

### Post by jonhill90 on 2008-02-11
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 502M   16M  487M   4% /lib/modules/2.6.22-14-generic/volatile
tmpfs                 502M   16M  487M   4% /lib/modules/2.6.22-14-generic/volatile
varrun                502M   88K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   72K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
tmpfs                 502M   12K  502M   1% /tmp

---

### Post by taurus on 2008-02-11
Did you try to run the first command in the previous post?

---

