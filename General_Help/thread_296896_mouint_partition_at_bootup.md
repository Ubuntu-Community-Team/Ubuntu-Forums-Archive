---
title: "mouint partition at bootup"
date: 2006-11-10
forum: General Help
---

### Post by feest on 2006-11-10
hi, ive made a partition to put games on it but i want it to be a mount point without the need of going to /media/sda4 but that i can directly acces it. i also want to mount it at bootup

gta sa has too little space left to install on my hdd, so i wanted it to install on my partition (sda4) so i said it should install there, but since this link **/media/**sda4 counts as a part of my primairy disk it thinks it hasn't enough space to install.

---

### Post by Choad on 2006-11-10
everything in unix is a subdirectory of root

/media/sda4 IS the partition, and has it's own filesystem and space

to mount it on boot you will need to add it to /etc/fstab

you dont have to mount it there however, you can mount it anywhere you want :)

---

