---
title: "usb card no access"
date: 2019-02-11
forum: General Help
---

### Post by matrooswolf on 2019-02-11
Hi, 
I have a usb micro 128GB card that I use to put music on for my RaspberryPi. But it stopped working overnight. When I put it in my computer, it registers under /media, but just for a second and then disappears. I can see it with Disks and with Gparted, I can see the UID, but I cannot 'play' it (I don't know the correct term in English, it's 'aankoppelen' in Dutch.) See picture attached.
[ATTACH=CONFIG]282470[/ATTACH]
Anybody any ideas?
Thanks,
Matroosje

---

### Post by Impavidus on 2019-02-11
The right word is that it fails to mount. This may be caused by filesystem damage. As it appears to be an ext4 filesystem, try fsck (with the sd card plugged in):```
sudo fsck /dev/mmcblk0p1
```Large SD cards are supposed to have the exfat filesystem (which is a proprietary format and therefore a bad choice as a standard), but your card has the ext4 filesystem. This may cause issues with some sd-card readers, but as your card worked before, I don't think that's the issue here.

---

### Post by matrooswolf on 2019-02-11
Thank you!```
sudo fsck /dev/mmcblk0p1
``` did the trick. This was the output by the way```
sudo fsck /dev/mmcblk0p1
[sudo] wachtwoord voor xxx: 
'fsck' uit util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/mmcblk0p1: herstellen van journal...
JBD2: Invalid checksum recovering block 6 in log
Controlesomfout in journal in /dev/mmcblk0p1
/dev/mmcblk0p1 is niet goed ontkoppeld, gedwongen controle.
Stap 1: Controle van inodes, blokken, en groottes
<fout> 5505026 <fout> tree (at level 1) could be narrower.  Repareren<j>? ja
<fout> 5505027 <fout> tree (at level 1) could be narrower.  Repareren<j>? ja
Stap 1E: Optimalisatie van extents-bomen
Stap 2: Controle van mappenstructuur
Stap 3: Controle van verbindingen tussen mappen
Stap 4: Controle van verwijzingsaantallen
Stap 5: Controle van groepssamenvattingen
Verkeerd aantal blokken (12610388, geteld=10744536).
Repareren<j>? ja
Verkeerd aantal inodes (7755418, geteld=7755363).
Repareren<j>? ja

/dev/mmcblk0p1: ***** BESTANDSSYSTEEM IS VERANDERD *****
/dev/mmcblk0p1: 51613/7806976 bestanden (0.5% niet-aaneengesloten), 20472360/31216896 blokken

```

I don't really know what all of that means, but it works again. So, thanks.

---

