---
title: "Flickering windows (ATI Radeon HD 2400 XT)"
date: 2008-05-01
forum: General Help
---

### Post by terrorsathan on 2008-05-01
-

---

### Post by terrorsathan on 2008-05-02
-

---

### Post by rossmoore on 2008-05-02
Others are having ATI and Hardy problems:
[http://ubuntuforums.org/showthread.php?t=765972](http://ubuntuforums.org/showthread.php?t=765972)

Everyone seems to be just waiting for an updated driver to be released...

Do you xserver-xgl installed? That certainly seemed to give a lot of people a big boost, although it didn't solve everything.

---

### Post by terrorsathan on 2008-05-02
-

---

### Post by Saint Angeles on 2008-05-02
fglrx works great for me (with aiglx, not xgl)
see if my mini-tutorial helps...

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

---

### Post by terrorsathan on 2008-05-02
-

---

### Post by Zorael on 2008-05-02
Which videocard drivers are you running?
```
$ lshw -C video
```

---

### Post by terrorsathan on 2008-05-02
-

---

### Post by Zorael on 2008-05-02
From what I can tell you're not running the proprietary driver.

Could you post the contents of your **/etc/X11/xorg.conf** file?

---

### Post by terrorsathan on 2008-05-02
-

---

### Post by Zorael on 2008-05-02
I don't see anything wrong with that xorg.conf.

Could you also post the contents of your **/var/log/Xorg.0.log** file?

---

### Post by terrorsathan on 2008-05-02
-

---

### Post by Zorael on 2008-05-02
Well, that's interesting.
```
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```
If I'm parsing it correctly, everything loads fine up until that point. Is this with drivers from the repositories, from envy or downloaded from the ATI site?

---

### Post by terrorsathan on 2008-05-02
-

---

### Post by terrorsathan on 2008-05-02
-

---

### Post by princcipepersia on 2008-09-01
I tried the newest and some old ATI drivers from their site and when I run I get this after I go through the gui app:

 Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.1 and later releases
Removing temporary directory: fglrx-install.J24534

Any clue?
thanks!

---

