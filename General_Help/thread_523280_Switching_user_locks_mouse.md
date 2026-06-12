---
title: "Switching user locks mouse"
date: 2007-08-11
forum: General Help
---

### Post by gruffbaby on 2007-08-11
Hey,

I have a problem that when I switch users, my mouse totally freezes. This happens as soon as the logon prompt appears. Pressing CTRL+ALT+F7 gets me back to original
screen and mouse movement again, but anyone know how to resolve this?

I'm new to Ubuntu 7.04, just installed it on Dell 9400 with ATI X1400 vid card (ooh the hardship) and managed to get Vodafone E220 modem (or Huawei E220) working although still have slight
problems with that,

Thanks in advance,
Gruffbaby

***P.S I've just had the problem also of the screen going blank, and the only way to get it back is to press CTRL+ALT+F9, then F7 so I guess this is related?

---

### Post by aum11 on 2007-08-29
I have the same problem which I get around by unplugging and replugging the usb mouse.

Any solutions?

---

### Post by tresni on 2007-09-07
Seems to be a known issue if the various bug reports are tracked.  Having it myself.  Anyway, relevant bug reports seem to be:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/134478](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/134478)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/60544](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/60544)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/134982](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/134982)
[https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/88152](https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/88152)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/68370](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/68370)

Unfourtantely no real news on a resolution yet.  One workaround that people say actually works is to Lock the screen of the first session and then use the password dialog presented to initiate switch users.  YMMV haven't tried it myself.

---

