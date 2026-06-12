---
title: "My KVM breaks input devices :("
date: 2008-03-17
forum: General Help
---

### Post by BassKozz on 2008-03-17
I use a KVM on my Ubuntu box and every time I switch back and forth using my KVM it messes up my input devices (Keyboard + Mouse).  Is there a way to fix this or issue a command via term that will re-associate my input devices and get them working back to normal?

Symptoms:
Shift keys -  stops working COMPLETELY
Caps Lock -  stops working COMPLETELY
Mouse Scroll Wheel  - stops working properly

All of these items are fine when I first boot, but as soon as I use the KVM to switch between different terminals/boxes these issues start to occur.
TIA,
-BassKozz

---

### Post by BassKozz on 2008-03-18
:bump:

---

### Post by dward526 on 2008-03-19
what is your kvm?

---

### Post by BassKozz on 2008-03-19
dlink [dkvm-4k]("http://www.dlink.com/products/?sec=0&pid=307")

i found out that it might not be my kvm after all, these seems to be happening w/out even using the kvm switch, after a while of use ubuntu doesn't work with shift keys or caps lock :confused:
btw, notice this whole post is in lowercase :( - i clicked on the smilies

p.s. i am running two instances of vmware running two winxp vm's and the shift and caps lock keys work in them even thou they aren't working in ubuntu--host

---

### Post by BassKozz on 2008-03-19
After further research, it looks like many others have had similar issues, so it's not due to my KVM after all...
Most people have been pointing to Compiz and SCIM as the culprit of this behavior, since I have Compiz turned OFF, it must be SCIM that is causing this...
Any idea's on how to resolve this and/or fix SCIM?

---

### Post by BassKozz on 2008-03-24
Fixed:
[http://ubuntuforums.org/showthread.php?t=729510](http://ubuntuforums.org/showthread.php?t=729510)

---

### Post by BassKozz on 2008-06-05
Found the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/195982](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/195982)

---

