---
title: "No windows decorations with Compiz w/ATI"
date: 2006-12-02
forum: General Help
---

### Post by RevengerPT on 2006-12-02
Hello. I've just installed official compiz 0.3.4, and when I try to enable GL destop, or type
```
gtk-window-decorator --replace & compiz --replace --use-cow gconf
```
window's borders just disappear. I'm running Ubuntu Edgy Eft with an ATI mobility x700 card. I'me using radeon open source driver.

Thanks for your help.
My best regards.

---

### Post by strabes on 2006-12-02
Are you using XGL? If so then run: ```
beryl-xgl
``` If that fixes the problem then add it to startup with gnome in gnome-session-properties.

With the open source driver you should be running AIGLX. Is there a particular reason you're using compiz instead of the newer beryl?

---

### Post by RevengerPT on 2006-12-02
I'm using AIGLX.
> **strabes said:**
> Is there a particular reason you're using compiz instead of the newer beryl?
I've already used beryl, but it is a litle slow, and I want to try out official compiz since I realy enjoyed it before the forking.

Can anyone help me?

My best regards.

---

### Post by RevengerPT on 2006-12-04
bump ](*,)

---

### Post by RevengerPT on 2006-12-05
Alright, I decided to use Beryl instead. When I start beryl, cpu is used on 100% most of the time, and X use to crash. Can anyone help?

It used to be stable with XGL and fglrx, but much slower. With radeon drivers, its faster, but has some bugs, like those above.

Thanks a lot.

---

### Post by strabes on 2006-12-05
add the following line to your xorg.conf's device section: ```
Option     "RenderAccel"   "true"
```

not sure if this will fix your problem. I've read about this problem elsewhere and it seems to be pretty common. Some searching on this website, wiki.beryl-project.org, and forum.beryl-project.org should land you a solution:

[http://www.ubuntuforums.org/showthread.php?t=295586&highlight=beryl+cpu+100%25](http://www.ubuntuforums.org/showthread.php?t=295586&highlight=beryl+cpu+100%25)
[http://www.ubuntuforums.org/showthread.php?t=288547&highlight=beryl+cpu+100%25](http://www.ubuntuforums.org/showthread.php?t=288547&highlight=beryl+cpu+100%25)
[http://www.ubuntuforums.org/search.php?searchid=10714024](http://www.ubuntuforums.org/search.php?searchid=10714024)

---

