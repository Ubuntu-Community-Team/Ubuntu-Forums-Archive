---
title: "problems with grip"
date: 2005-07-09
forum: General Help
---

### Post by 89c51 on 2005-07-09
i instaled grip using the ubuntu deb package everything went ok but i have these two problems

1)when i insert a cd to play it i have no sound (when i use the gnome cd player everything works  OK) even thought it seems like grip is actualy playing the track (time)

2)the cd riping is very slow (1x) 
i tried enabling the dma with sudo hdparm -d1 /dev/hda (where hda is the cdrom) but got the following message

/dev/hda:
setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permited
using_dma  =  0 (off) 

any help will be usefull

---

### Post by titus1950 on 2005-07-10
[QUOTE=89c51]i instaled grip using the ubuntu deb package everything went ok but i have these two problems

1)when i insert a cd to play it i have no sound (when i use the gnome cd player everything works  OK) even thought it seems like grip is actualy playing the track (time)

2)the cd riping is very slow (1x) 
i tried enabling the dma with sudo hdparm -d1 /dev/hda (where hda is the cdrom) but got the following message

/dev/hda:
setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permited
using_dma  =  0 (off) 

any help will be usefull[/QUOTE]
     



Read this  [http://www.ubuntuforums.org/showthread.php?p=93238#post93238](http://www.ubuntuforums.org/showthread.php?p=93238#post93238)   

it worked for me...

---

### Post by 89c51 on 2005-07-20
the hdparm problem was solved 

but the sound problem remains :-?

---

