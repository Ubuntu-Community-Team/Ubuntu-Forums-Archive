---
title: "Plain vanilla boring termnal login"
date: 2006-09-29
forum: General Help
---

### Post by Fred Doolie on 2006-09-29
Stupid title, huh?

How do I boot up (Gnome) Ubuntu into a plain white on black text screen?
I mean the one you get if you just install a server version; no GUI or graphics at all. The "Geek" method,

I tried the terminal and failsafe modes on the GDM login but they give me a little black on white window in the corner of the screen.

Thanks

---

### Post by yopnono on 2006-09-29
Did you do a server install? What packages did you install.

---

### Post by baldy1324 on 2006-09-29
well yes a server install wont install a gui but you cant change that so heres how to start into the console
install sysv-rc-conf ```
sudo apt-get install sysv-rc-conf
```
now run sudo sysv-rc-conf and scroll down with your cursor to the gdm line, then use your space to take the X off every entry on your line. now reboot and good 'ol console!

---

