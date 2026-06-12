---
title: "Acer C720 - Touchpad not working?"
date: 2014-12-24
forum: General Help
---

### Post by harry28 on 2014-12-24
After following a guide this [wiki,]("https://wiki.archlinux.org/index.php/Acer_C720_Chromebook") I managed to instal Linux Ubuntu 14.10 on my Acer C720 chromebook. I knew before installing I would have issues with the hotkeys (volume, brightness etc.) and the trackpad. I got the hotkeys working after installing a package, however after following the guide on the wiki I cannot get the trackpad to work. When looking at [this]("http://help.ubuntu.com/community/SynapticsTouchpad") page on the ubuntu website and running "xinput list" I get this:

```
user@chrubuntu:~$ xinput list
Virtual core pointer                        id=2    [master pointer  (3)]
Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
Logitech USB Receiver                       id=12    [slave  pointer  (2)]
Logitech USB Receiver                       id=13    [slave  pointer  (2)]
Virtual core keyboard                       id=3    [master keyboard (2)]
Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
Power Button                                id=6    [slave  keyboard (3)]
Video Bus                                   id=7    [slave  keyboard (3)]
Power Button                                id=8    [slave  keyboard (3)]
Sleep Button                                id=9    [slave  keyboard (3)]
Sleep Button                                id=10    [slave  keyboard (3)]
HD WebCam                                   id=11    [slave  keyboard (3)]
AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]



```

and there is no mention of a trackpad or ADB mouse. How do I go about installing the trackpad drivers for my Acer C720? Also instead of creating a whole new thread, when I shut the lid of my laptop (to put it to sleep), it goes to sleep fine however when I lift the lid again, the laptop comes back on but the screen doesn't so I have to force shutdown with the power. How do I fix this also?

---

### Post by harry28 on 2014-12-24
Managed to sort it. After I upgraded the kernal to the latest version, 3.18, the trackpad works fine without installing anything else. If any one else is having this issue then just upgrade the kernal since apparently Ubuntu doesn't come with the latest version.

---

### Post by russoue on 2015-04-21
Thanks. I installed the latest 3.18 kernel and it fixed everything for me!

---

