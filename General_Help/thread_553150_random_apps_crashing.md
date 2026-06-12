---
title: "random apps crashing"
date: 2007-09-17
forum: General Help
---

### Post by abstractism on 2007-09-17
okay, I managed to get my linux machine to be stable long enough for an ubuntu install. what I'm not sure of now is why apps like firefox and rhythmbox just dump out for whatever reason(like a force quit), and gnome has done it once as well(resulting in having to log back in).

I already ran about 8 hours worth of memtest86+, with zero errors, so I'm kinda stumped here. 
My current h/w specs are:
DFI Infinity RS482 motherboard
AMD FX-55 (San Diego core)
1GB OCZ DDR500
BFG Tech Geforce 7800GT OC
Soundblaster Audigy SE

---

### Post by Shazaam on 2007-09-17
Post the output of
sudo fdisk -l   (small L)

---

### Post by abstractism on 2007-09-17
isn't fdisk just for formatting though?

---

### Post by ddrichardson on 2007-09-17
> **abstractism said:**
> isn't fdisk just for formatting though?No fdisk is for partioning and returning information on drives.

Have you checked your temperatures?

---

### Post by Shazaam on 2007-09-17
> **abstractism said:**
> isn't fdisk just for formatting though?

Sorry senior moment there. What I need to know is how full your partitions are. A full /home (separate) partition will cause your problems. And ddrichardson has a good question.

---

### Post by abstractism on 2007-09-17
I'll check this after work tonight, but as they're totally new installations(everything reformatted and such) I don't see the HD being much more than 15-20% capacity on a 300GB drive.

---

