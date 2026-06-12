---
title: "Virtual CD-RW Drive"
date: 2008-05-03
forum: General Help
---

### Post by AdrianStrays on 2008-05-03
Does anyone know of a Virtual CD-RW Drive? One that will simulate the burning of a CD, and then allow me to rip from it?

---

### Post by CorvisRex on 2008-05-03
Depends.  You can always simply mount the iso image, linux being linux and not windows, by using:
mount -o loop -t iso9660 file.iso /mnt/location

And it just works like any other mounted file system,  but if you encounter any weird file system types, etc, you can also check out AcetoneISO2, which pretty much works like any other virtual drive app.  I have used it once or twice to deal with odd disk image types.

raven

---

