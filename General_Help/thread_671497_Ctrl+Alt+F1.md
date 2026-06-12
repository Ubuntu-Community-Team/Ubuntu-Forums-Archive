---
title: "Ctrl+Alt+F1"
date: 2008-01-18
forum: General Help
---

### Post by Kaphix on 2008-01-18
I accidentally pushed Ctrl+Alt+F1, screen went black, restarted, every time it goes past bootscreen its black. I saw many topics on this, but none like mine;

I can't type, so I can't do startx
Ctrl+Alt+F6/7 doesn't work

---

### Post by PinkFloyd102489 on 2008-01-18
Hit Alt+F1 to bring up the console, log in, and start X back up.

---

### Post by Kaphix on 2008-01-18
Nothing happened immediately afterwards, but when I restarted the kernel failed to load and I got a grub console. I'm just going to reinstall, I backed up the files I needed to my PSP. I would still like a solution though, in case it happens again.

---

### Post by dimbulb1024 on 2008-01-18
Have to try it. What is the command to start x back up?

---

### Post by lgambett on 2008-01-18
Sorry friends, no need to restart the X server. Simply press ALT + F7 et voilà... the graphical console is back. Linux has six virtual character terminal, from ALT + F1 to ALT + F6, and (at least) one graphical terminal, ALT + F7. From a graphical terminal you need to press CTRL + ALT + Fn.

---

### Post by danwood76 on 2008-01-18
> **dimbulb1024 said:**
> Have to try it. What is the command to start x back up?

you type startx funnily enough :)

regards,
Danny

---

### Post by bodhi.zazen on 2008-01-18
> **lgambett said:**
> Sorry friends, no need to restart the X server. Simply press ALT + F7 et voilà... the graphical console is back. Linux has six virtual character terminal, from ALT + F1 to ALT + F6, and (at least) one graphical terminal, ALT + F7. From a graphical terminal you need to press CTRL + ALT + Fn.

Actually there are 6 graphical servers as well :)

Ctrl-Alt-F7 - F12

You can start multiple X sessions or ssh -X on these additional graphical consoles.

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

Or, if you like :

xinit -e ssh -XCT user@server gnome-session -- :1 

xinit -e ssh -XCT user@server fluxbox -- :2

---

### Post by Christmas on 2008-01-18
Yeah and as far as I know, you can make many more just by modifying /etc/inittab.

---

