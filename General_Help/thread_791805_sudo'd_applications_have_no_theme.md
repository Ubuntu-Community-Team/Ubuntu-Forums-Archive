---
title: "sudo'd applications have no theme"
date: 2008-05-12
forum: General Help
---

### Post by mailbox on 2008-05-12
...and just appear with the default, blocky, ugly theme. I remember fixing this on my old 7.04 install (using 8.04 64bit with xfce right now), and it was something very simple, like *ln -s something somewhere*... I just don't remember the locations. Can anyone help?

---

### Post by ShodanjoDM on 2008-05-12
I think that's because the theme you've installed is in your home folder's .theme directory. As it is, if you use sudo to launch a GUI application, it won't recognize the theme and fallback to the default instead.

There are atleast two solutions that I can think of. First do use gksudo instead of sudo to launch a GUI application as root but with user's set theme.

Second, this involves a little bit more work. Move all the themes and icons you have inside your .themes and .icons directories to /usr/share/themes and /usr/share/icons respectively.

I prefer the second method, and actually have always installed themes and icons/cursors that way since every user accounts will have the same themes & icons to choose with.

---

### Post by FuturePilot on 2008-05-12
This should do it
```
sudo ln -s ~/.themes /root/.themes
```
and it works for icons too :)
```
sudo ln -s ~/.icons /root/.icons
```

> **ShodanjoDM said:**
> 
There are atleast two solutions that I can think of. First do use gksudo instead of sudo to launch a GUI application as root but with user's set theme.

That won't make a difference. Using gksudo doesn't change anything with the theme. But you really should be using gksudo for graphical apps anyway.

---

### Post by mailbox on 2008-05-12
Ah, thanks to both of you, that was exactly what I was looking for!
I know I should be using gksudo, but I "have" to sudo all my apps; if I use gksudo, the system will hang for ten seconds, then let me input my password in the little box, then hand for twenty or so seconds, then do whatever. This is happenening to my friend on his 32bit 7.10 install as well.

---

