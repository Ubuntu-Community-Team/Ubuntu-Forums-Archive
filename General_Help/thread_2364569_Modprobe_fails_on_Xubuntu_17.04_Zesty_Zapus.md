---
title: "Modprobe fails on Xubuntu 17.04 Zesty Zapus"
date: 2017-06-24
forum: General Help
---

### Post by Ralph L on 2017-06-24
I am trying to follow instructions from a website that suggests that I can improve touchpad performance by doing the following: ```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
```However, modprobe doesn't seem to work. The first command doesn't even disable my touchpad.  If I do the same test on Xubuntu 16.04, it immediately disables the touchpad, and I must issue the second command (with or without the proto parameter) to get the touchpad to work again.
Anybody got any idea why I can't make modprobe work on 17.04 (zesty)???

---

### Post by oldos2er on 2017-06-25
Could you please link to the website you're following?

---

### Post by Ralph L on 2017-06-25
Web site is:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1026046](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1026046) Post # 36.  Thank you for responding.  Your help is appreciated....

---

