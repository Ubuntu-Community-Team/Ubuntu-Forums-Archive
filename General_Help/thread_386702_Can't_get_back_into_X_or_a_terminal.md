---
title: "Can't get back into X or a terminal"
date: 2007-03-17
forum: General Help
---

### Post by WetWired on 2007-03-17
Hey all, I've messed it up big time now. lol. I completely changed hardware, and now, naturally, I can't get back into Ubuntu. I know exactly what the problem is, but I can't get to a termial to fix it. I need to change my bus id for my video card. X won't start, and I can't get it to drop me back to a terminal. I've tried starting with the CD, but it hangs on mounting root filesystem. So I can't even reinstall. I'd like to completely reinstall anyway, is there a way I can do this without too much hassle?

---

### Post by taurus on 2007-03-17
Can you boot into recovery mode from GRUB menu?  Then edit /etc/X11/xorg.conf with

```
nano -Bw /etc/X11/xorg.conf
```

---

### Post by WetWired on 2007-03-17
No, I can't even use recovery mode. It hangs and gives me a strange error saying "nobody cared". lol. Not sure what that means.

---

### Post by taurus on 2007-03-17
I don't even know what that error message is.  And you said you can't even boot with the LiveCD!

Did you replace mobo, video card, and the whole thing on your machine?

---

### Post by WetWired on 2007-03-17
I replaced everything but the hard drives. Completely new machine.

---

### Post by WetWired on 2007-03-17
I finally got back into X. I just hit ALT+F1 and got to a terminal, now almost all is well. lol

---

