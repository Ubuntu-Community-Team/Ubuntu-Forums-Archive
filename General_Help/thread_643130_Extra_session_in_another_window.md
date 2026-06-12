---
title: "Extra session in another window"
date: 2007-12-17
forum: General Help
---

### Post by Kazur on 2007-12-17
I am going to make a few screen casts soon, and since I use a higher resolution than the ones who are going to watch the screen casts, I want to make them smaller. I don't want to change the resolution of my screen, so I'm looking for a software that will let me log into an extra session in a window. Something like VNC and VMware, just that I want it to be ran from my own computer. I also have to have 3d-support.

---

### Post by TidusBlade on 2007-12-17
I dont know if this is what your looking for, but i use KDE, so I can start another session, and I use ALT+CTRL+F7 for example to switch to it, and there I can change to the resolution I want...

---

### Post by Kazur on 2007-12-17
And my resolution will stay the same as I left it when I'm going back to my main session?

---

### Post by bingoUV on 2007-12-17
VNC does not stop you from connecting from the same machine. I do that all the time. Not sure about 3d though. You can use unlimited resolution, but you will have to scroll if your VNC session resolution is higher than the host session. 

Running another full blown X server will give you pretty much everything (3d, resolutions etc.) that you get on your primary session. Run the following from command terminal (ctrl - alt - F1)
```

xinit -- :1.0 

```

---

### Post by Kazur on 2007-12-17
I found [this]("http://ubuntuforums.org/showthread.php?t=271674") guide, and it works very well. Currently running Gnome + XFCE.

Thank you.

---

