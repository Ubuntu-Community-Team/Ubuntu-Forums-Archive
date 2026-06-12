---
title: "Can not copy files from ubutu drive to Flash memory"
date: 2012-12-17
forum: General Help
---

### Post by babakflame on 2012-12-17
Dear Buddies
Hi 
I can't copy files from ubuntu drive to my flash memory. When I copy the file, The paste icon is inactive on my flash memory. How can I fix it?;)

---

### Post by sudodus on 2012-12-17
Maybe you have no write access to the flash memory. It could be either a hardware switch (on the card) or software permission flags.

Try the following commands in a terminal window, and paste the output into a reply.

```
cat /etc/mtab
```

```
ls -l /media/your-flash-drive
```

(substitute the appropriate directory for the partition on your flash drive)

---

### Post by babakflame on 2012-12-17
Dear sudodos
Hi
The outputs are as the following:

babak@babak-VPCEA26FG:~$ cat /etc/mtab
/dev/sda7 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/babak/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=babak 0 0
/dev/sdb1 /media/96ECC483ECC45F5D ntfs ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks 0 0
babak@babak-VPCEA26FG:~$ ls -l /media/96ECC483ECC45F5D 
total 8
dr-x------ 1 babak babak 4096 2012-12-17 16:58 GRI_3
dr-x------ 1 babak babak    0 2012-12-03 13:43 PolimiH2_1006
dr-x------ 1 babak babak 4096 2012-12-16 16:53 SANDIA_CH4H2N2

Thnks):P

---

### Post by fdrake on 2012-12-17
```

sudo umount /dev/sdb1
sudo mkdir /media/usb
sudo mount -t ntfs-3g /dev/sdb1 /media/usb

```

---

### Post by coffeecat on 2012-12-17
> **babakflame said:**
> /dev/sdb1 /media/96ECC483ECC45F5D [COLOR="Red"]ntfs ro[/COLOR],nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks 0 0

It looks as though you've uninstalled the read-write ntfs-3g driver somehow. If the ntfs-3g driver was in use, the bit I've highlighted in red would read "fuseblk rw". At the moment your system is using the read-only kernel ntfs module.

Check Software Centre or Synaptic. Re-install ntfs-3g if it is missing and then your ntfs flash drive will be automounted read-write when next you plug it in. 

By the way, which version of Ubuntu are you running?

---

### Post by babakflame on 2012-12-18
Dear coffeecat
Hi
 I did as u mentioned and my problem solved. Iam using ubuntu 11.10 (oneiric ocelot).

Thnks
 Bye):P

---

