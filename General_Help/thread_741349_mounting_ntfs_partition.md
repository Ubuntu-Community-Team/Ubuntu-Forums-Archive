---
title: "mounting ntfs partition"
date: 2008-03-31
forum: General Help
---

### Post by monica77 on 2008-03-31
Hi,
It is one month I've moved from windows to xubuntu, and so I still need access to my old ntfs partition. I didn't have problems to access to the windows' files until yesterday.
I think the problem started when I modified my network configuration ,more precisely, my host name in an attempt to configure my ISP because as soon as I did it ubuntu froze, and once I could log out and then log in, my desktop changed.
I changed back my host name for which I think it was the original one, but cannot be sure since I can not recall well; however, once I logged in again my desktop went back to normal, but I cannot access anymore to my ntfs partition.

Browsing on the internet I found that editing /etc/fstab will allow me to have access again to the partition; however, I'm little bit scared about changing the file since I don't know if an improper change could risk ubuntu.

Executing sudo nano /etc/fstab, I get the following:

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=f43c529c-8fa8-4f1a-aa15-0fac821958a1 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=ECF0E363F0E3328E /media/hda1 ntfs defaults,umask=007,gid=46 0 1
# Entry for /dev/hda5 :
UUID=f13a09c1-a2b1-4165-afba-382183d0b155 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

Does anyone know how can I mount again the partition, and also if the change of the host name could be the cause of not being able to access to my old unit?


Thanks a lot!!
M77

---

### Post by pieisgood4589 on 2008-03-31
I'd suggest just strictly following modifying fstab, just do everything the guide tells you to do and Ubuntu will be fine.

---

### Post by monica77 on 2008-03-31
What instruction?

---

### Post by monica77 on 2008-03-31
I could mount it using the graphic interface storage device manager, without knowing any of these lines

roc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=f43c529c-8fa8-4f1a-aa15-0fac821958a1 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=ECF0E363F0E3328E /media/hda1 ntfs defaults,umask=007,gid=46 0 1
# Entry for /dev/hda5 :
UUID=f13a09c1-a2b1-4165-afba-382183d0b155 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

but i cannot edit files in the ntfs unit

---

