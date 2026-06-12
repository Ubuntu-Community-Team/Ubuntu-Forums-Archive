---
title: "Is there a way to auto-generate an fstab file?"
date: 2007-01-23
forum: General Help
---

### Post by mdurham on 2007-01-23
The title says it all really.
Cheers, mike

---

### Post by chochem on 2008-04-24
a bit of thread necromancy... anybody? I've just created a new extended partition with quite a few logical ones inside and would rather have an fstab made for me, replete with uuid etc. than hack one together myself...

---

### Post by ebelog on 2008-04-24
If your system is running, and the drives you are concerned about are currently mounted, then you could start with the /etc/mtab file, which is a table of all the currently mounted filesystems.

```
mv /etc/fstab /etc/fstab.bak
cp /etc/mtab /etc/fstab
vi /etc/fstab
```

Keep a backup of the original file for reference, because you'll have to add back any devices which aren't currently mounted (cdrom, floppy, etc). Plus, if something goes wrong, you can put the original fstab file into place.

------------------------------
[http://www.ebelog.com](http://www.ebelog.com)

---

### Post by dcstar on 2008-04-25
> **chochem said:**
> a bit of thread necromancy... anybody? I've just created a new extended partition with quite a few logical ones inside and would rather have an fstab made for me, replete with uuid etc. than hack one together myself...

Install the **pysdm** package and let it write the fstab entries - it won't use UUID but you can muck around with that yourself.

---

### Post by chochem on 2008-04-26
Thanks for the replies... It isn't exactly install-like auto-generation but I guess this is more useful anyway. pysdm is a nice fstab-gui-editor with a few handy explanations (saves me having to switch back and forth between a web page for reference and a text editor) so I guess I'll hang onto that.

---

