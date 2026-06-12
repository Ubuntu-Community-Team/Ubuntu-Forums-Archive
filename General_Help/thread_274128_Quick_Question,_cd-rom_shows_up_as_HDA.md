---
title: "Quick Question, cd-rom shows up as HDA"
date: 2006-10-09
forum: General Help
---

### Post by Michaeldaley on 2006-10-09
Ubuntu has been operating flawlessly for me for about 6 months.  Recently I went to checksum a dvd I made and I noticed that my dvd-rom shows up as /dev/hda.  Is this normal on a SATA system?  Is it just going to the next available label, i.e., since the harddrive is /dev/sda is the dvd /dev/hda because it is the next available label?  

Let me know if this will cause any problems, or if I should just adjust to this setup and remember that /dev/hdc = /dev/hda

Thanks in advance

---

### Post by anaconda on 2006-10-09
It just means that you CD is the first (and propably only) IDE drive in your system.

If it has previously been hdc the "c" is just an accident.. and it meand that the CD was the first IDE-device in your secondary IDE-controller. ie. the "c" has nothing to do with CD..

Ide evices are "numbered" hda, hdb, hdc, hdd.. etc
SATA and USB and SCSI-devices are numbered sda, sdb, sdc, sdd... etc

Dont worry it is normal and wont cause you any problems.

---

### Post by Michaeldaley on 2006-10-09
Thank you for the help.  :-D

---

