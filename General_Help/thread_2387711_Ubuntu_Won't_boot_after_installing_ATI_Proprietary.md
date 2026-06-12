---
title: "Ubuntu Won't boot after installing ATI Proprietary Drivers."
date: 2018-03-22
forum: General Help
---

### Post by russianmoney on 2018-03-22
[COLOR=#333333][FONT=Ubuntu]Hello. First of all, i'm using an old ATI GPU (Radeon HD 5450). I Tried installing the drivers on 16.04, but they aren't supported, causing me to not be able to find fglrx on the default Repos. I Downgraded to Ubuntu 14.04, and after following the Tutorial [Here]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]And Restaring My pc freezes on the boot screen. i can't access the Terminal with ALT+CTRL+F1 too. I Reinstalled Ubuntu 14.04 about 6 Times today already, trying to download fglrx from their website and running it and i still got the same problem. 
Linux is the only operating system i can use ATM. And it's so sad that i can't play my games properly on it.
Seriously though, Any help will be really, really, appreciated.
Thanks[/FONT][/COLOR]

---

### Post by deadflowr on 2018-03-22
Which 14.04 version?
The latest version cannot run the drivers since it uses the same hardware and kernel stack that 16.04 uses.
To install the drivers on 14.04 you need this version
[http://old-releases.ubuntu.com/releases/14.04.1/]("http://old-releases.ubuntu.com/releases/14.04.1/")
(even though the page says 14.04.2 the version you would be getting is 14.04.1 which uses the original hardware stack for 14.04.
that hardware stack is what will work.)

---

### Post by russianmoney on 2018-03-23
I'm using the latest version of 14.04.
Is it possible to downgrade from it?

---

### Post by Bashing-om on 2018-03-23
russianmoney; Yepper ^^ .

*downgrade* your trusty to the original trusty 3.13 kernel and xorg :
```

sudo apt install --install-recommends linux-generic xserver-xorg-core xserver-xorg xserver-xorg-video-all xserver-xorg-input-all libwayland-egl1-mesa

```

reboot into grub and choose to boot the 3.13 kernel .

Now if all is good remove the unwanted HWE stack:
```

sudo apt purge linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial

```

verify once more that grub is happy
```

sudo update-grub

```

All good ?? Now you can install the FGLRX driver.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2018-03-25
> **russianmoney said:**
> Linux is the only operating system i can use ATM. And it's so sad that i can't play my games properly on it.

Why can't you use the default open source radeon driver? It used to work fine on my HD4550.
fglrx/Catalyst is a dead end.

---

