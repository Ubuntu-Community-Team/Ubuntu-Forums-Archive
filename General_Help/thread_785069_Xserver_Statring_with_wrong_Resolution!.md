---
title: "Xserver Statring with wrong Resolution!"
date: 2008-05-07
forum: General Help
---

### Post by killall-9 on 2008-05-07
Hello!

My Xserver starting always with 1600x1200 Resolution,i want that change to 1280x1024!When i set with Nvidia configuration tool or manuel  with "xrandr -s" on 1280x1024 Xserver dont remeber for next start !

---

### Post by ryanhaigh on 2008-05-07
In nvidia-settings when you run it using gksudo nvidia-settings you can click the save configuration to xorg.conf button (at least its something like that) this should make your changes permanent.

---

### Post by killall-9 on 2008-05-08
Thx that work fine!

The Important command for your "xorg.conf" in "Section Screen" is   

Option         "metamodes" "1280x1024_85 +0+0"

---

