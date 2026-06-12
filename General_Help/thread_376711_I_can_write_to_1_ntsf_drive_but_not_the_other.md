---
title: "I can write to 1 ntsf drive but not the other"
date: 2007-03-05
forum: General Help
---

### Post by Bubs on 2007-03-05
this is strange to me.  

I have 1 external usb hard drive.  I bought the case and drive separate put it together and formated in windows a few years back.  I can't get NTFS write support on it.  I can read it but now write to it.

I just bought a new WD external hard drive 120g for $99 straight out of the box I plug it in and can write to it.

why can't I write to the other?  I have ntfs-3g installed and I just reformatted it to ntfs again under linux but I still can't write to it.

any suggestions?  I would rather not reformat to fat or vfat.  and I want to be able to go from linux and windows easily

---

### Post by Jussi Kukkonen on 2007-03-05
Are they mounted the same way? *cat /etc/mtab* will tell you.

---

### Post by Bubs on 2007-03-05
nope.  but I found the problem.  the new WD I bought was preformatted to vfat.  thats why I can write to it.

so let me ask you this..  Is vfat a good fs?

---

### Post by Jussi Kukkonen on 2007-03-06
> **Bubs said:**
> nope.  but I found the problem.  the new WD I bought was preformatted to vfat.  thats why I can write to it.

so let me ask you this..  Is vfat a good fs?

No, not really. It has ancient limitations (like a 2GB file size limit which means e.g. videos must be chopped in to pieces) and is not very fault-reliant. Generally speaking it is inferior to NTFS. However, I'm not sure this is the case in linux use. I have not used either filesystem for several years now, but I do know that fat is at least tried and tested over the years (and as filesystems go, that is a very important thing). My impression is that NTFS is still somewhat unknown...

---

