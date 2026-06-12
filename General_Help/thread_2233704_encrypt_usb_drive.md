---
title: "encrypt usb drive"
date: 2014-07-10
forum: General Help
---

### Post by sn0m on 2014-07-10
Hi guys
For whatever reason, I need to encrypt a whole usb drive without formating it.
Is there any way of doing it?
Thanks
sn0m

---

### Post by kurt18947 on 2014-07-10
The tricky part may be encrypting without formatting.  If you could copy the contents, format and move the contents back I have what seems like a pretty simple solution.  I installed "cryptsetup" from the repositories.  Now I can plug a flash drive in, open the 'disks' app, select the drive, click the little star or cog in the upper right corner and one of the options is format & create an encrypted file system.  This does require SUDO privileges.  I don't think this is cross-platform if that matters.  Another option I'd considered but I'm uncertain about the strength of security is to create a .7z archive and be sure to encrypt the file names.

---

