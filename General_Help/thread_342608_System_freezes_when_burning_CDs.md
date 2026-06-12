---
title: "System freezes when burning CDs"
date: 2007-01-20
forum: General Help
---

### Post by Andrej_BB on 2007-01-20
I am using edgy with Gnome.
Whenever i try to burn either data, or .iso the system freezes (i can still move my mouse cursor around but that's about it.. )
It happens at least twice during the burning process, first at initialization and the second one, when CD is being finished. Sometime it freezes in between as well. It's very annoying

How can i fix that ?

---

### Post by wpshooter on 2007-01-20
What CD burning program are you using ?

---

### Post by Andrej_BB on 2007-01-21
Whatever is the default. 
For example, when burning ISO, i just right click burn to disk...

---

### Post by happy-and-lost on 2007-01-21
The Nautilus CD burner is still a bit buggy. I recommend Brasero for all your burning needs (Available via Automatix, might be in the repos)

---

### Post by g8m on 2007-01-21
Did you check if DMA is on on the burner. (hdparm). If it's off, burning is slow and it makes your system slow.

 hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

---

