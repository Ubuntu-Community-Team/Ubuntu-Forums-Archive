---
title: "New ATI card"
date: 2007-02-27
forum: General Help
---

### Post by Jphenow on 2007-02-27
Installed my new ATI 9250 card today, installed *fglrx-control* and *xorg-driver-fglrx* that is all I have done, I know I must be missing something since when I go to the ATI control it says the driver doesn't have the firegl x11 extensions, then the manager shows up with next to nothing on it. Also wondering if I will need to completely reconfigure my beryl since originally I had it setup with an nvidia card, if so does anyone have any idea what the easiest rout to that is?

---

### Post by renzokuken on 2007-02-27
could you post your xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Mateo on 2007-02-27
run this:

```
fglrxinfo
```

it will tell you if fgl is working.  If it says something about MESA drivers, your fglrx isn't set up.

by the way this is a good page for setting it up, if it's not already working.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

