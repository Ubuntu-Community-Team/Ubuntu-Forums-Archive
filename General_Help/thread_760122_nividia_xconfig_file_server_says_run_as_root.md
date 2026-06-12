---
title: "nividia xconfig file server says run as root?"
date: 2008-04-19
forum: General Help
---

### Post by nacho32 on 2008-04-19
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server

that what it tells me?

---

### Post by x1a4 on 2008-04-19
Hit Alt+F2 on your keyboard to open the Run dialog, then execute 'gksudo nvidia-xconfig'.  When prompted enter your password.

---

### Post by nacho32 on 2008-04-19
i did that and it opens a untitled blank page?

---

### Post by nacho32 on 2008-04-20
this is what it says
 'file:///home/jeff/&apos;gksudo%20nvidia-xconfig'

---

