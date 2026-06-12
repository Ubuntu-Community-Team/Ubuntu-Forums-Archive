---
title: "USB flash drive appearing automatically"
date: 2008-02-02
forum: General Help
---

### Post by bayne on 2008-02-02
Hello, I am looking to make my USB drive appear on my desktop when I plug it in. It's mounting correctly, but it doesn't appear on my desktop until I open it from Computer under places.

Im using gutsy, on a Dell latitude d620, if it matters.

---

### Post by mbrush on 2008-02-02
In gconf-editor, under Apps>Nautilus>Desktop, enable "volumes-visible"

not sure if you have to logout/in to have the changes take effect.

Good Luck

---

### Post by bayne on 2008-02-02
It's already enabled.

---

### Post by dcstar on 2008-02-02
> **bayne said:**
> Hello, I am looking to make my USB drive appear on my desktop when I plug it in. It's mounting correctly, but it doesn't appear on my desktop until I open it from Computer under places.

Im using gutsy, on a Dell latitude d620, if it matters.

Have you by any chance added things to your /etc/fstab file?

---

### Post by bayne on 2008-02-02
No i have not.

---

### Post by dcstar on 2008-02-02
> **bayne said:**
> No i have not.

Open a terminal and enter this command after you plug it in, then post the last screen of output:
```
dmesg
```

Also check System-Preferences-Removable Drives and Media-Storage and make sure the top two boxes are ticked.

---

### Post by bayne on 2008-02-02
Guys, the USB is appearing, and I can access it, but I want it to appear automatically, but it does not appear on my desktop until I open the file manager and explore it.

---

### Post by bayne on 2008-02-02
mm.

---

