---
title: "Low Graphics Mode???"
date: 2012-12-13
forum: General Help
---

### Post by tjamscad on 2012-12-13
I work at a shop that has several computers that get the "low graphics mode" error. What causes this and how do i fix it?

---

### Post by grahammechanical on 2012-12-13
I had that once. The graphics card was overheating.

---

### Post by dannyboy79 on 2012-12-13
it can be due to a driver conflict or because you upgraded your kernel and need to reinstall the driver? Need more information. What version of ubuntu are you using? What is the graphics card be used and what driver are you using?

---

### Post by tjamscad on 2012-12-13
> **dannyboy79 said:**
> it can be due to a driver conflict or because you upgraded your kernel and need to reinstall the driver? Need more information. What version of ubuntu are you using? What is the graphics card be used and what driver are you using?

How do I find out that information?

---

### Post by dannyboy79 on 2012-12-13
to find out graphics card there are several ways, one is to run this command within a terminal session
```
lspci
```

to find out what graphics driver you can try this command
```
cat /etc/X11/xorg.conf | grep Driver
```

also, you can copy and paste the entire contents of this file /var/log/Xorg.0.log at pastebin and then paste the link here (forums don't like it when you paste a ton of code directly so that's what pastebin is for)

---

### Post by tjamscad on 2012-12-13
They are running 10.04 LTS.

lspci output:
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

shop@shop-computer:~$ cat /etc/X11/xorg.conf | grep Driver
cat: /etc/X11/xorg.conf: No such file or directory

shop@shop-computer:/etc/X11$ cat /etc/X11/xorg.conf.failsafe | grep Driver
Returns Driver "fbdev"

---

