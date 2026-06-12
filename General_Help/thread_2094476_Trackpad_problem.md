---
title: "Trackpad problem"
date: 2012-12-13
forum: General Help
---

### Post by zeroaesthetics on 2012-12-13
Hi everyone,

I installed Ubuntu 12.10 on my Macbook Pro Retina 13", everything works fine, except the trackpad.

I can move my cursor around and a left click is working. The problem is scrolling and a right click. Is there any way I can get them to work?

Thanks in advance,
0A

---

### Post by Rexilion on 2012-12-14
Try installing (or starting):

```
gpointing-device-settings
```

It's the tool used to modify trackpad settings.

---

### Post by zeroaesthetics on 2012-12-14
Thanks for the reply Rexilion,

unfortunately, it didn't work.

Some users say that two-fingers scrolling works fine on MBP 15" Retina since they upgraded to 12.10.

Is there anything else I should try?

---

### Post by Rexilion on 2012-12-15
As a last resort, this is what I always have to do on my laptop to get sane settings:

```
synclient TapButton1=1 TapButton2=2 TapButton3=3
```

It's a pretty stupid command, but it's mentioned everywhere and it works. If it works for you, then you could add it to Xorg.conf to make it permanent. But first, try this.

---

