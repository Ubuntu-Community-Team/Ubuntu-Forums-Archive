---
title: "HICOLOR (16-bit)"
date: 2006-11-07
forum: General Help
---

### Post by xenoalien on 2006-11-07
How do I change my desktop to HICOLOR (16-bit)? :-k

---

### Post by CatKiller on 2006-11-07
```
sudo nano /etc/X11/xorg.conf
```

PageDown to the Screen section and change **DefaultDepth 24** to **DefaultDepth 16**. Save the file and exit (Ctrl-O, Ctrl-X), close any open programs and press **Ctrl-Alt-Backspace** to restart X.

---

### Post by xenoalien on 2006-11-07
The file is a read only file... How do I change it to read and write so that I can edit it?

---

### Post by CatKiller on 2006-11-07
> **xenoalien said:**
> The file is a read only file... How do I change it to read and write so that I can edit it?

**sudo nano /etc/X11/xorg.conf**. I'm sure I said. Or **gksudo gedit /etc/X11/xorg.conf** if you like the Notepad-style interface for some reason. Or **kdesu kate /etc/X11/xorg.conf** if you're using Kubuntu. You might want to read these:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by xenoalien on 2006-11-07
Thanks! It worked. I just didn't know how to save with sudo nano.

---

### Post by CatKiller on 2006-11-07
Glad you got it fixed. For reference, it's Ctrl-O to save - it'll ask you the name you want to call the file, just press Enter to leave the name unchanged - and Ctrl-X to exit. The keyboard shortcuts are printed at the bottom of the screen.

---

