---
title: "Formatting USB drive."
date: 2013-03-17
forum: General Help
---

### Post by noob2141 on 2013-03-17
HI, I JUST DOWNLOADED UBANTU AND FORMATTED MY USB TO EXT3, BECAUSE I NEEDED TO PUT FILES IN IT. I USED GPARTED PATRITION EDITOR AND IT'S NOW AN EXT3. I TRIED TO PUT MY ITEMS IN IT, BUT  IT SAYS THE OWNER IS ROOT SO I DON'T HAVE PERMISSION. I SEARCHED AROUND FORUMS AND FOUND TERMINAL THINGSS...
I TRIED THIS: 
1.[FONT=monospace]sudo blkid
2.gksudo gedit /etc/fstab
3.UUID=<uuid>     /place/to/mount     ext3     defaults    0     2
4.sudo mount -a
5.sudo chown <username>:<username> /place/to/mount
I MANAGED TO GET TO STEP 3 BUT I GOT STUCK AT "/PLACE/TO/MOUNT" WHAT DOES THAT MEAN???
AND WHAT DOES "DEFAULTS 0    2" MEAN? AND WHAT IS "SUDO MOUNT -A"
PLESAEEEE HELP ME 
(ARE THERE EASRIER WAYS TO GET ACCESS?)

[/FONT]

---

### Post by carl4926 on 2013-03-17
Why not format it to FAT?

---

### Post by mörgæs on 2013-03-17
Please don't use caps-lock. It equals shouting.

---

