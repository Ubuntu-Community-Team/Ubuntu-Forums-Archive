---
title: "How to execute a terminal command at boot"
date: 2013-05-26
forum: General Help
---

### Post by chewy84 on 2013-05-26
What i want to do is get this custom screen resolution with xrandr to  run at every boot so i don't have to enter it myself or copy and past it  this is the code i want to run at every boot


```
cvt 800 600 60 && xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync && xrandr --addmode TV1 800x600_60.00 && xrandr --output TV1 --mode 800x600_60.00
```

i don't really want to play around editing configure/files just a nice easy
script that will execute after or during every boot.

---

### Post by MG&amp;TL on 2013-05-26
I think you mean every *login, *rather than every *boot*. X isn't running for most of boot-time, so the command will probably fail.

If that's the case, then we need to know your desktop environment to make any progress. Thanks!

---

### Post by chewy84 on 2013-05-26
Yeah at login would be better cheers for that.

I'm using ubuntu 12.04LTS

---

### Post by MG&amp;TL on 2013-05-26
> **chewy84 said:**
> Yeah at login would be better cheers for that.

I'm using ubuntu 12.04LTS

I'll assume the Unity environment, then.

In which case, press Alt-F2 then type:

```
gnome-session-properties
```

You should get a popup dialog with options for configuring startup options. :)

---

### Post by chewy84 on 2013-05-26
Thanks that sorted it nice one :D

---

