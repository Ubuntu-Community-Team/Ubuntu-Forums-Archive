---
title: "Help with building my own Ubuntu"
date: 2007-12-22
forum: General Help
---

### Post by alexj.powell on 2007-12-22
Hi I'm having some problems with making my own custom Ubuntu iso. I'm using Ubuntu 7.10 x86 desktop.

As a base I'm using the same distro as above. I called the iso gutsy.iso
In terminal I have used the following commands to get as far as I have.


---------------------------------------------------------------------------------------------------------------------

sudo bash

mkdir /mnt/loop
mount -o loop gutsy.iso /mnt/loop

mkdir ubuntu-rebuild
rsync -ax /mnt/loop/. ubuntu-rebuild

umount /mnt/loop

mount ubuntu-rebuild/casper/filesystem.squashfs /mnt/loop -t squashfs -o loop

mkdir ubuntu-source
rsync -av /mnt/loop. ubuntu-source
umount /mnt/loop

cp /etc/resolv.conf ubuntu-source/etc/
chroot ubuntu-source

After I type in chroot ubuntu-source it comes up with the following error:

id: cannot find name for group ID 1002

I've tried everything I can think of, but the error remains.

Help please. :(

---

### Post by alexj.powell on 2007-12-22
Please help, I've search google with no answers...

---

### Post by Rui Pais on 2007-12-22
Hi,
have you checked the permissions of files /etc/passwd and /etc/group? It should be (both):
```
-rw-r--r-- 1 root root ...
```

Since it looks for user 1002 (a 3rd user!!) you must have copied something from your actual installation to the chrooted one with incorrect permissions/ownership (cp without -a or equivalent flag of a file system or cp _with_ that flag of a file owned by 1002 user, maybe)

hth

---

