---
title: "Hal/Gnome configuration"
date: 2004-11-10
forum: General Help
---

### Post by shu on 2004-11-10
Hi!

Can anybody tell how is the whole hal being configured? I mean, how does it happen that my /dev/hda4 mounted under /mnt/media shows up in nautilus as 'media'? On my slackware box it shows up as 'put_my_disk_serial_number_here' instead of 'media' and I would really like to get the same thing there.

Sorry, if it's to much off topic, but I can't find any valuable info on this topic in the internet and you guys have it running. ;-)

Thanks in advance
shu

---

### Post by ashley_v on 2004-11-10
[QUOTE=][/QUOTE]
 umount -l /dev/hda4 && mkdir /mnt/put_my_disk_serial_number_here ; mount /dev/hda4 /mnt/put_my_disk_serial_number_here

Then edit /etc/fstab so it mounts it there on boot.

Your question was a bit vague but hope that helped.

---

### Post by shu on 2004-11-11
I have my disk mounted as /mnt/media. My problem is that it's being shown in gnome as "WDC-WB800jB-....." where it should be "Media". And I don't know what is wrong with my setup.

---

