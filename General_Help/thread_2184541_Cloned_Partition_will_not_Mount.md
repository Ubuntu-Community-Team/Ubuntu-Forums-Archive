---
title: "Cloned Partition will not Mount"
date: 2013-10-29
forum: General Help
---

### Post by Redalien0304 on 2013-10-29
Cloned my Ubunu13.04 Partition, will not mount now? But will mount in Gparted? Used Gparted 16 on usb Stick, Cloned my Ubuntu 13.04 Partition to a USB Drive. They do both have the same  UUID. I think that is reason it wil not Mount ? (Except in Gparted)

---

### Post by sudodus on 2013-10-29
That might be the problem. What do you want to do with the cloned copy?

---

### Post by Redalien0304 on 2013-10-29
just a Backup now & upgrade test to Ubuntu 13.10. Do not want my main system to 13.10 since it stall has issues.

---

### Post by sudodus on 2013-10-29
Yes, that is a good strategy.

If you wish, you could test the backup by booting from it (when the internal drive, the source of the cloning is disconnected). Or if no proprietary drivers, you can test the backup in another computer.

I usually make an image instead of a cloned copy with Clonezilla. The image is a compressed file, containing the clone, and there is no UUID conflict.

---

### Post by Redalien0304 on 2013-10-29
Ok ty sudodus, but should i cahnge the UUID? so i can view my Files in 13.04? Cause i can awlays use the Cloned Partition, if my Partiton Goes? Right?

---

### Post by sudodus on 2013-10-29
If you only change the UUID of a root partition, it won't work properly. You need to adjust the entries in certain files too, **/etc/fstab** and **/boot/grub/grub.cfg** and maybe also some other file, for example **/etc/grub.d/40_custom** if you have tweaked that file.

---

