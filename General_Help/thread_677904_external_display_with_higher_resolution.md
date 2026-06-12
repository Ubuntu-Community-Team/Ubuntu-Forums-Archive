---
title: "external display with higher resolution"
date: 2008-01-25
forum: General Help
---

### Post by buttari on 2008-01-25
Hi all,
I just got a new laptop (dell D630) with a replicator and an external 20" screen capable of doing 1600x1200. The resolution (correctly) detected for the laptop built-in screen is 1440x900 but when I plug it on the replicator I cannot do more than 1024x768 on the external screen. How do I add higher resolution? do I really have to manually edit xorg.conf?
Thanks

Alfredo

---

### Post by taurus on 2008-01-25
You can edit /etc/X11/xorg.conf manually

```
gksudo gedit /etc/X11/xorg.conf
```
or you can reconfigure your X server again.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, you can restart X with <Ctrl><Alt>Backspace.

What kind of graphic card does that laptop have?

---

### Post by buttari on 2008-01-31
> **taurus said:**
> You can edit /etc/X11/xorg.conf manually

```
gksudo gedit /etc/X11/xorg.conf
```
or you can reconfigure your X server again.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you are done, you can restart X with <Ctrl><Alt>Backspace.

What kind of graphic card does that laptop have?

Taurus,
sorry for the late reply. Yes I modified xorg.conf and it worked. However it is quite strange that ubuntu doesn't have a cleaner way to achieve such an easy task. This may be really discouraging for somebody who doesn't want/know to mess around with files in /etc
Thanks a lot however

Alfredo

---

