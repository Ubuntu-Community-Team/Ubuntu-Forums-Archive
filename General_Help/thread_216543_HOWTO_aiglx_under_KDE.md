---
title: "HOWTO: aiglx under KDE"
date: 2006-07-15
forum: General Help
---

### Post by eruditescholar on 2006-07-15
Hi, I've been using XGL on Gentoo on my desktop, and just installed kubuntu on my laptop and noticed the lack of guide for aiglx under KDE. To install aiglx to kde follow guides on installing aiglx and compiz.

(for KDM)
then:
change ServerCmd in /etc/kde3/kdm/kdmrc to: (use 1 instead of 0 for ATI cards)
> ServerCmd=/usr/bin/Xorg-air :0

(for KDE)
and add:
> KDEWM=compiz-start
to /etc/environment

I'm running on Intel graphics its fast and stable enjoy.

---

### Post by soul_rebel2 on 2006-07-18
hmmm cant make it work for me...

i have installed xserver-xorg-air and compiz-kde from universe/multiverse, but i dont have compiz-start und when i try to start compiz manually it tells me i have no composite extensions.
in my xorg.conf, i do have " Option "AIGLX" "true"" in serverlayout and i have these sections:

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
 Option "Composite" "Enable"
EndSection

i have an i915 graphicschip and 3d-acceleration works otherwise...

thanks for help!

---

### Post by exhuma.twn on 2006-08-10
I have exactly the same problem.

I also tried the above mentioned config settings, and after that, KDE refused to start up. Also fvwm-crystal failed, but fvwm (vanilla) started. After removing both lines again, the WM's started up fine again.

---

### Post by exhuma.twn on 2006-08-10
Tracked it down to the following line:

```
ServerCmd=/usr/bin/Xorg-air :0
```

As soon as I made that modification, X crashed as soon as I started up a WM. Changing back to the original value made it work again. Obviously without aiglx support though.

---

### Post by exhuma.twn on 2006-08-10
I got it working following this: [http://ubuntuforums.org/showthread.php?t=145068](http://ubuntuforums.org/showthread.php?t=145068)

Note: the "dist-upgrade" is important!

Have fun.

---

