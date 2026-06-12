---
title: "X11 not configured correctively"
date: 2007-01-20
forum: General Help
---

### Post by tjb891 on 2007-01-20
I have the nvidia drivers installed with my geforce 4 mx 4000 and somehow 3d acceleration has been turned off. Can anyone tell me how to turn it back on. I attached my xorg.conf file

---

### Post by fenian on 2007-01-20
In the Device section change Driver "nv" to Driver "nvidia".

---

### Post by der_joachim on 2007-01-21
Also make sure that the restricted modules are installed with the correct version.

---

