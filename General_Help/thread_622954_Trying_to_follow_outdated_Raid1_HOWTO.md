---
title: "Trying to follow outdated Raid1 HOWTO"
date: 2007-11-25
forum: General Help
---

### Post by scram69 on 2007-11-25
Hi-

I'm trying to follow the howto in /usr/share/doc/mdadm/rootraiddoc.97.html (also found online at [http://alioth.debian.org/frs/download.php/668/rootraiddoc.97.html](http://alioth.debian.org/frs/download.php/668/rootraiddoc.97.html)) to move my system to RAID1.

I'm making good progress until I reach steps 5.1-5.3 which deal with configuring Lilo to boot on the newly created raid1.  AFAIK, Ubuntu uses Grub instead - and therefore, I need to do something analogous in /boot/grub/menu.lst.

Unfortunately, I'm not having success modifying menu.lst.  From things I've read, I'm guessing I need to modify the boot entry to point my new hd (/dev/hdc), but I have no idea what to put in the hd(#,#) entry.  If I use hd(1,0) and reboot, grub boots on my original drive (hd(0,0)).  What's worse, /dev/hdc does not appear in /boot/grub/device.map.  

Looking at the HOWTO, does anyone know what should be done for step 5.1-5.3 for Ubuntu?  Or, can anyone point me to an updated version of the HOWTO?

Thanks-

---

