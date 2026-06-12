---
title: "30&quot; HP LP3065c and Nvidia 8800 GT resolution cant go 2560x1600"
date: 2008-02-16
forum: General Help
---

### Post by vor111 on 2008-02-16
okay, i got the nvidia drivers by envy... but now i cant use 2560x1600. it falls at 2048x1536, and i cant choose anything higher...Nvidia settings are the same! ...help

Horizontal scan 100 KHz

Vertical scan 60 Hz

2560 x 1600 @ 60 Hz (native aspect ratio of 16:10)

---

### Post by dcstar on 2008-02-17
> **vor111 said:**
> okay, i got the nvidia drivers by envy... but now i cant use 2560x1600. it falls at 2048x1536, and i cant choose anything higher...Nvidia settings are the same! ...help

Horizontal scan 100 KHz

Vertical scan 60 Hz

2560 x 1600 @ 60 Hz (native aspect ratio of 16:10)
```

sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

### Post by vor111 on 2008-02-18
Worked like a charm! thanks!

---

