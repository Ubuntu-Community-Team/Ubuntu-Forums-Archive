---
title: "Ubuntu freezes at logout and shutdown"
date: 2018-03-18
forum: General Help
---

### Post by zuccagabriele97 on 2018-03-18
Hello everyone.

Recently, when try to logout or shutdown my pc, it freezes: i can only see the background image. Most of the times, I have to press the power button in order to shutdown the pc.
I'm running Ubuntu 16.04 on an Asus x556UR.

```
$ uname -a
Linux laptop-gabriele 4.13.0-36-generic #40~16.04.1-Ubuntu SMP Fri Feb 16 23:25:58 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

```
$ apt-cache show xserver-xorg | grep Version
Version: 1:7.7+13ubuntu3
```

When I try to shutdown by tipying ```
sudo shutdown -h now
``` in tty1, this is what i see: [https://drive.google.com/file/d/1LSvSZEbr3PbyL4wOOcz1Xf-_y4IcYyJt/view?usp=sharing](https://drive.google.com/file/d/1LSvSZEbr3PbyL4wOOcz1Xf-_y4IcYyJt/view?usp=sharing)

---

### Post by ank2 on 2018-03-18
Uh oh. I once had this but not when shutdown. It took a kernel update to fix that. May be sit and wait is the solution here?

How long did you wait before pressing the power button? May be leave it alone for a long time and see if it recovers.

---

