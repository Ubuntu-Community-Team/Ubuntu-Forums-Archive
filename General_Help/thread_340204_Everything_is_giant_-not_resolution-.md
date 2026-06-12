---
title: "Everything is giant?? -not resolution-"
date: 2007-01-16
forum: General Help
---

### Post by BillyR on 2007-01-16
So, i only have one resolution, and i dont know how to get more.
but everything is too big. i  restarted my computer, and everything got giant.
now i cant see all the icons on my desktop, even.
and its not like its the font.
the font is fine , and can be changed, in firefox and stuff. but everything else is giant!
anyone know whats going on??
thanks.

---

### Post by dcstar on 2007-01-16
> **BillyR said:**
> So, i only have one resolution, and i dont know how to get more.
but everything is too big. i  restarted my computer, and everything got giant.
now i cant see all the icons on my desktop, even.
and its not like its the font.
the font is fine , and can be changed, in firefox and stuff. but everything else is giant!
anyone know whats going on??
thanks.

What "resolution"?, what exactly are you referring to??

---

### Post by BillyR on 2007-01-16
my screen resolution (640 X 180) is the only resolution i can have.
how do i get more resolutions?
and everything is like, zoomed in. 
everything is giant.

---

### Post by bodhi.zazen on 2007-01-16
Well, it sounds (looks ?) like a resolution problem to me :p

Try this (you may need to switch to tty1 and log in)

To get to tty1:

Hit Ctrl-Alt-F1

you should now be at the command line , enter:```
sudo dpkg-reconfigure -phigh xserver-xorg

```

Then change to your GUI - Ctrl-Alt-F7

Re-start X - Hit Ctrl-Alt-Backspace

If that does not work,

what video card and monitor are you using ?

---

