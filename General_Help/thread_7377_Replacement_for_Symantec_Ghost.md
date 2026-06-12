---
title: "Replacement for Symantec Ghost"
date: 2004-12-06
forum: General Help
---

### Post by bazuka on 2004-12-06
Is there a package out there that functions as a replacement for Symantec Ghost? I apted mondo, but I can't figure out how to get it to work.

---

### Post by jeremy on 2004-12-07
I use partimage.

---

### Post by gregp on 2004-12-07
I'm using g4u. Very easy and works great.

[www.feyrer.de/g4u](www.feyrer.de/g4u)

---

### Post by bazuka on 2004-12-07
Unfortunately, neither of those worked for me.

Partimage: Won't let me image /dev/hda1 because it's mounted, and I can't unmount it. I tried to apt-get it from the Live CD, and that failed. I then tried through Helix, and that didn't work either.

G4U: The .iso image they provide is not bootable.
  note: when I try to open the iso with Archive Manager, I get this: "isoinfo: Unable to find Joliet SVD"


Any other suggestions?

---

### Post by jeremy on 2004-12-07
Sorry forgot to mention, I use partimage with knoppix.

---

### Post by killerfish on 2004-12-07
[QUOTE=jeremy]Sorry forgot to mention, I use partimage with knoppix.[/QUOTE]
 I use True Image from Acronis and have successfully used it to image/restore/resize Linux partitions.  If you also have Windows installed, you can to the 'work' from there.  Otherwise, it has the capability to create a bootable CD to do everything.   Only downside is that it's not free....! :)

---

### Post by bazuka on 2004-12-07
[QUOTE=jeremy]Sorry forgot to mention, I use partimage with knoppix.[/QUOTE]
 Thanks man, worked great. A little slow, but that's my processor's fault, really.

---

### Post by jeremy on 2004-12-08
Glad it works for you. I really can't understand why partimage is not included in the Warty live cd, hopefully it wiill be in Hoary.

---

### Post by one_ro on 2005-09-08
[QUOTE=bazuka]Is there a package out there that functions as a replacement for Symantec Ghost? I apted mondo, but I can't figure out how to get it to work.[/QUOTE]

Hit the following command in a console: [COLOR=Red]**sudo mondoarchive**[/COLOR] 
I assume you typed just [COLOR=Red]**mondo**[/COLOR] (as I did).

---

### Post by khalil on 2005-09-15
[QUOTE=killerfish]I use True Image from Acronis and have successfully used it to image/restore/resize Linux partitions.  If you also have Windows installed, you can to the 'work' from there.  Otherwise, it has the capability to create a bootable CD to do everything.   Only downside is that it's not free....! :)[/QUOTE]


i have used to same program and found it to be quite easy to operate and user friendly

---

