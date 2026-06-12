---
title: "xubuntu fonts resize"
date: 2007-01-25
forum: General Help
---

### Post by jmvidalvia on 2007-01-25
I installed Xubuntu twice, and had the same problem:

1- I install xubuntu
2- Fonts appear in Sans 9: view is great and perfect
3- I complete the instalation with many other programms form repositories (codecs, pdf, java, etc...).
4- I restart.
5- Fonts now look very small.
6- I increase them up to Sans 12: I feel I see them a little bit worse than at the bigining, but it works.
7- I open Firefox: **Menu looks now very big!** Horrible
8- Other programs look ok.

Any Idea about:
¿why appearance changes alone in system?
¿why Firefox menu looks so big? ¿how to fix it?

Many thanks!!

---

### Post by jmvidalvia on 2007-01-25
It seems this is related with dpi.

xdpyinfo | grep resolution
resolution: 75x75 dots per inch

¿does anybody know how to modify dpi in edgy+xfc4?
Thanks!

---

### Post by tiger487 on 2007-02-05
Hi,

I got the same problem and you're right : it's a problem about resolution.

To solve it, I used the indications given here : [http://xubuntulinux.blogspot.com/2006/07/ubuntu-set-correct-dpi-for-x-server.html](http://xubuntulinux.blogspot.com/2006/07/ubuntu-set-correct-dpi-for-x-server.html)

So to summary it, you have just to put this in your *~/.config/xfce4/Xft.xrdb* file :

```
Xft.dpi: 96
```

---

### Post by jmvidalvia on 2007-02-06
Yes, I did it.
I also had to add this:
DisplaySize 338.67 211.67
to my Monitor Section in xorg.conf.
Thanks!

---

