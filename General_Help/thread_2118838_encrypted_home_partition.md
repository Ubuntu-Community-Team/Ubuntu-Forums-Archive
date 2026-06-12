---
title: "encrypted home partition"
date: 2013-02-22
forum: General Help
---

### Post by canistel on 2013-02-22
I'm trying to setup encrypted home partition; I have the correct entry in /etc/crypttab, the correct entry in /etc/fstab, and have loaded "dm-mod" and "dm-crypt" in /etc/modules. However, during boot i'm not asked for my password, and /dev/mapper/linux-encr-home device is never created. I have to manually run "cryptsetup luksOpen /dev/sda4 linux-encr-home" and then mount my home dir. So it only works when run manually after boot, not during boot process...

Any ideas? I've done this before so I'm sure it's just something I'm forgetting somewhere...

---

### Post by rcayea on 2013-02-22
I can't help with personal knowledge, so I went looking and found this HOWTO, recommended by the Ubuntu docs site. Hopefully it helps. 

[http://ubuntuforums.org/showthread.php?t=1449168](http://ubuntuforums.org/showthread.php?t=1449168)

---

### Post by canistel on 2013-02-25
Thanks for the link... unfortunately though that looks like a different setup; I'm using luks and that looks like ecryptfs.

---

