---
title: "Wine Desktop"
date: 2007-06-16
forum: General Help
---

### Post by shadows85 on 2007-06-16
How can I resize the Wine Desktop? I cant seem to do anything with it, its too small for configuration or anything I want to use it with.... My video card is a ATI Radeon 200.

---

### Post by kimusabi on 2007-06-16
Open up a terminal and type in 
```
 winecfg 
```
 And click on the Graphics tab. Check the window emulation box and set the size to whichever you want. I prefer using 800x600, depending on what programs I'm running.

---

### Post by shadows85 on 2007-06-16
> **kimusabi said:**
> Open up a terminal and type in 
```
 winecfg 
```
 And click on the Graphics tab. Check the window emulation box and set the size to whichever you want. I prefer using 800x600, depending on what programs I'm running.


Winecfg it self is in wine desktop and I cant choose anything.

[http://i86.photobucket.com/albums/k96/ShadowReaper1983/Screenshot-1.png](http://i86.photobucket.com/albums/k96/ShadowReaper1983/Screenshot-1.png)

---

### Post by kimusabi on 2007-06-16
Odd. Wonder how that happened. Anyway I suppose what you could do is open up the wine configuration file ( /home/username/.wine/user.reg) and change the window resolution there. It's at the end of the file.
```
[Software\\Wine\\X11 Driver] 1181674510
"Desktop"="yourcurrentwindow" <--- change to 800x600
"DesktopDoubleBuffered"="N"
"DXGrab"="N"
"Managed"="N" 
```

---

### Post by dnzz on 2007-06-16
```
winecfg
```

After clicking to grafics press tab key 9 times and write 800 then press one more time and write 600 then press enter.

It will change the desktop to 800x600

---

### Post by kimusabi on 2007-06-16
That would only work providing Shadow checked the Emulate Desktop box. Wine has done that to me a few times in the past. But it's worth a go I suppose.

---

### Post by shadows85 on 2007-06-16
thanks you two :popcorn:

---

