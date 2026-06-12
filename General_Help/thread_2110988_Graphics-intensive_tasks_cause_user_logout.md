---
title: "Graphics-intensive tasks cause user logout"
date: 2013-01-31
forum: General Help
---

### Post by makanaken on 2013-01-31
Hi, im new here. i been using ubuntu for about 1 year in my notebook Samsung SENS R530. i dont know why, but im having a problem. When im watching a movie, using facebook apps, playing games, etc. My ubuntu just log out by it self and put me in the log in screen. And all my stuff restart like crashed applications (firefox crash report). It seems like it "crashes" all the time im using applications that needs more resources.
How can i fix this? Does somebody else experiencing this?

thx for the help

---

### Post by papibe on 2013-01-31
Hi makanaken. Welcome to the forums ):P

What version of Ubuntu are you using?

Do you update/upgrade your machine often?

Regards.

---

### Post by makanaken on 2013-01-31
thx papibe. im using ubuntu 12. i update it all the time.

---

### Post by oldos2er on 2013-01-31
Changed thread title to more accurately reflect the problem.

---

### Post by papibe on 2013-01-31
It may be this bug: [Random log off in Ubuntu 12.04 LTS]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/980519").

What is your graphic card? If you don't know, please post the result of this command:
```
lspci -nnk | grep -iA2 vga
```
Are you using the Nvidia proprietary driver?

Regards.

---

### Post by makanaken on 2013-01-31
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c06d]
    Kernel driver in use: i915

i think the "random log off problem" is the one, im reading it

---

