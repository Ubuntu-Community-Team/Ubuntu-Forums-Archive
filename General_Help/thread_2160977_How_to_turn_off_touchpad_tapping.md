---
title: "How to turn off touchpad tapping"
date: 2013-07-09
forum: General Help
---

### Post by JimS on 2013-07-09
...
Lubuntu 13.04 doesn't seem to be able to turn off touchpad "tapping".
Synaptic Package Mgr says "Synaptics TouchPad driver for X.Org server" is installed.
But I can't find it.
And I can't turn off "tapping".

New HP2000 laptop w/ Win8, Ubuntu 12.10, LinuxMint15, and Lubuntu13.04 installed.
Other distros were no problem with turning off tapping.
...

---

### Post by kalehrl on 2013-07-09
```
sudo nano /etc/xdg/lxsession/Lubuntu/autostart
```
at the bottom add:
```
@synclient MaxTapTime=0
```
reboot or log out.

---

### Post by JimS on 2013-07-13
Thanks,
But I think with all the other issues
I've seen with Lubuntu
I'll dump it in the trash bin.
LinuxMint 15 xfce
is so very much better put together.

---

