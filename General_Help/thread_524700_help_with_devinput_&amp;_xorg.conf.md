---
title: "help with /dev/input/ &amp; xorg.conf"
date: 2007-08-13
forum: General Help
---

### Post by adam_r on 2007-08-13
hi,

i have a laptop, so my usb logitech mouse sometimes is connected and sometimes isnt.
anyway i setup in xorg.conf so it will use the "evdev" module which works great.

my problem - the number of the /dev/input/event keeps changing! now i thought i solved it with putting in  /etc/udev/rules.d/20-names.rules:

```
KERNEL=="event[0-9]*", SYSFS{name}=="Logitech USB Receiver", SYMLINK+="input/vxrev"
```

and it did make a symlink! a correct one everytime! so what is the problem - I DONT KNOW!: stupid xorg.conf is not willing to work with the symlink! i dont understand why.

Option		"Device"	"/dev/input/event4" - WORKS
Option		"Device"	"/dev/input/vxrev" - Dont Work

and...
```
adam@adam-laptop:/dev/input$ ls -al vx*
lrwxrwxrwx 1 root root 6 2007-08-13 19:42 vxrev -> event4
```

Can someone help me please? i looked at all the related threads....
[B]
SOLVED: instead of "vxrev" i called the symlink "event10" and it worked[/B]

---

### Post by kidders on 2007-08-14
Hi there,

Just in case you're in any doubt, your solution is the correct one. This is a stupid limitation of Xorg, which has been around for some time ... fixing it must be more complicated than it seems like it should be!

---

