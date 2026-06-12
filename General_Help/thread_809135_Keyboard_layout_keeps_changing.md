---
title: "Keyboard layout keeps changing"
date: 2008-05-27
forum: General Help
---

### Post by achelis on 2008-05-27
Hi

My keyboard layout has started to sometimes change to English. I can get it back by going to System->Preferences->Keyboard and change any setting, but having to this is getting a bit annoying. Danish is the only layout I have enabled though.

Any ideas to what's causing this/how to fix it?

---

### Post by SyL on 2008-05-27
Hi,

this might be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/196277](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/196277)

---

### Post by achelis on 2008-05-27
Quite possibly. However my problem is kinda different: In the bug report the Keyboard layout doesn't change when it's supposed to, in my scenario it changes when it's not supposed to.

But thanks for the pointer.

---

### Post by jamescbjr on 2008-12-08
> **achelis said:**
> Quite possibly. However my problem is kinda different: In the bug report the Keyboard layout doesn't change when it's supposed to, in my scenario it changes when it's not supposed to.

But thanks for the pointer.

Edit: /etc/X11/xorg.conf, if you only want danish change us to danish.  Works for me.  Hope this helps.

---

