---
title: "black and white boot up screen"
date: 2006-11-28
forum: General Help
---

### Post by dracule on 2006-11-28
I have had a black and white boot up/shut down screen ever since I installed my system. I have a 64 bit system and want this to go away.

---

### Post by taurus on 2006-11-28
Just put "quiet splash" at the end of an entry for the "kernel" in /boot/grib/menu.lst...

```

title Ubuntu (2.17.6)
root (hd0,0)
kernel /boot/vmlinuz-1.17.6 root=/dev/ha1 ro **quiet splash**
initrd /boot/initrd-1.17.6-img
blah
blah

```

---

### Post by dracule on 2006-11-28
will this make it go completely away? because I just want it to be color.

---

### Post by taurus on 2006-11-28
Brown background with process bar...

---

### Post by xopher on 2006-11-28
This is an amd64 bug with edgy.

Here's a link to the bug: [https://bugs.launchpad.net/distros/ubuntu/+source/usplash-theme-ubuntu/+bug/67545](https://bugs.launchpad.net/distros/ubuntu/+source/usplash-theme-ubuntu/+bug/67545)

---

### Post by dracule on 2006-11-28
I read evertying, and it doesnt lok like I can do much.

---

### Post by thoffland on 2006-12-26
I've noticed the same thing. I just installed Edgy today on my 64bit system and saw that. I never would have known the difference if I wasn't running it on my laptop. It is a bugger.

---

