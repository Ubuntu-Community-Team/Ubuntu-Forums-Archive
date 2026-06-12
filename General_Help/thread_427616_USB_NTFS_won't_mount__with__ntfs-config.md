---
title: "USB NTFS won't mount  with  ntfs-config"
date: 2007-04-29
forum: General Help
---

### Post by alexjhill on 2007-04-29
Hey guys i cant see here if this has been answered looked at a lot of posts.

I have USB stick NTFS format and i have installed ntfs-config and ntfs-3g

if i select Apps>>systmes tools>> ntfs config tools.

Set the enable write - 

when mounting the USB it says it is unable to mount the volume. I put in the following to my /etc/fstab file 

/dev/sdb1/media/ALEX'S USB ntfs-3g defaults,force 0 0

as suggested by the error but that doesn't work. I can see the stick contents fine / it mounts if i un-check the "enable write" options.


Any ideas?

Thanks!

---

### Post by alexjhill on 2007-05-03
in the end i reformatted the stick as FAT and all works fine.

---

