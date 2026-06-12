---
title: "VirtualBox no bootable medium found"
date: 2007-02-04
forum: General Help
---

### Post by Rich78 on 2007-02-04
Hi,

I've setup VirtualBox on my machine but everytime it runs I get "no bootable medium found"

I'm trying to get it to boot my MSDN DVD disc so I can install WinXP on it.

I have tried unmounting the DVD from my host machine, and also checking the mount CD/DVD Drive in the settings.

But I still get the same problem.

The CD/DVD is mounted to /dev/cdrom on my host drive, it was the only option in the drop down so I don't know if this is correct?

---

### Post by Rich78 on 2007-02-04
Ok I think I've found out what it is, it's mounting /dev/cdrom when my host drive is /dev/dvd because it has a dvd loaded.

Does anyone know how to make VirtualBox point to /dev/dvd instead?

Thanks

---

### Post by Rich78 on 2007-02-04
Anyone?

---

### Post by lbyrd33 on 2007-02-13
Im not at my actual computer right now, but if I can remember correctly under setting you could directly point to whatever your cdrom location was. If I am mistaken, you can also try funning directly with an iso file of the cd.

---

### Post by Rosskat on 2008-03-19
I was having exactly the same problem with my PC.

Eventually, I uninstalled virtualbox completely. I then double clicked on the .deb file in the file browser and installed it the automated way (previously I installed it using the terminal). Then magically my dvd drive appeared in the list of CD/DVD drives and it started working.

I dunno if that helps.

Good Luck! :)

---

