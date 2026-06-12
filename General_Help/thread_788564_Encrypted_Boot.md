---
title: "Encrypted Boot"
date: 2008-05-09
forum: General Help
---

### Post by CyberGuard on 2008-05-09
I'm wanting to encrypt my hard drive. I've read tutorials and such on using loop-AES and LVM to do this but I dont think it does what I want. I'm wanting to make a keyfile (AES 256 bit randomly generated key) and put it on a CD (my computer wont boot from USB. Then set it up so the CD needs to be present in the drive before the computer will boot up. I'm a security freak and want to lock down my laptop. I've read some posts were people would create just an encrypted partition. I wouldnt be asking this if I knew how to do this. Thanks for any help
EDIT: hope this is in the right forum.

---

### Post by storm99999 on 2008-05-09
You don't need to boot from the usb key, it just needs to be plugged in in most guides I've read as long as the /boot directory is installed separately.
What should happen is this:
```

Grub
 |
 v
/boot (finds the kernel, not encrypted)
 |
 v
Wait for USB to be plugged in
 |
 v
Decrypt / and /home and swap
 |
 v
Boot

```

All that I have read uses some specific method of interrupting the system until the usb drive is plugged in, but as for using a CD anyways, I do not think I can help much.

---

