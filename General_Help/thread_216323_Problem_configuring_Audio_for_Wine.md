---
title: "Problem configuring Audio for Wine"
date: 2006-07-15
forum: General Help
---

### Post by dhruv_1884 on 2006-07-15
Hi,

I uninstalled wine and reinstalled it , then ran 

winecfg

and as soon as i click on the audio tab, the coniguration window crashes, and this is what gets displayed at the terminal

dhruv@dhruv-desktop:~$ winecfg
__driCreateNewScreen_20050727 - succeeded
__driCreateNewScreen_20050727 - succeeded
Creating link /home/dhruv/.kde/socket-dhruv-desktop.
can't create mcop directory
dhruv@dhruv-desktop:~$
](*,) 

wonderin what i should do


thanks 
regards 

dhruv

---

### Post by starseeka on 2006-09-15
I had the same problem. A little searching around in the wine bug reports showed that if you rename or move the file /usr/lib/wine/winearts.drv.so that it would work. I tried it, and winecfg stopped crashing.

Hope this helps.

Now I just need to figure out what drivers I need to select to get sound working. :)

Starseeka

---

### Post by dhruv_1884 on 2006-09-15
Thanks dude, it worked, really good work, keep it up
=D> 

regards

dhruv

---

