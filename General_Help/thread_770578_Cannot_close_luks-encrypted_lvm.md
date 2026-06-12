---
title: "Cannot close luks-encrypted lvm"
date: 2008-04-27
forum: General Help
---

### Post by Meson on 2008-04-27
I have an encrypted partition that contains a logical volume group.  After running:```
user@ubuntu:~$ sudo cryptsetup luksOpen /dev/sda3 sda3_crypt
```

These entries appear in my mapper:```
user@ubuntu:~$ ll /dev/mapper
total 0
crw-rw---- 1 root root  10, 63 2008-04-27 09:55 control
brw-rw---- 1 root disk 254,  6 2008-04-27 10:24 lvm-lvm_root
brw-rw---- 1 root disk 254,  5 2008-04-27 10:24 lvm-lvm_swap
brw-rw---- 1 root disk 254,  4 2008-04-27 10:24 sda3_crypt
```

So each logical volume is obviously being automatically setup (via udev I believe).

Now, if I try to close the encrypted partition:```
user@ubuntu:~$ sudo cryptsetup luksClose sda3_crypt
Command failed: Device busy
```

I'm figuring it has something to do with the fact that the logical volumes aren't being automatically closed.  Any suggestions?  Also, what is /dev/mapper/control?

---

### Post by kwutchak on 2008-12-07
De-activate any logical volumes on the device.  For example:

vgchange -an /dev/vgCloseMe

---

