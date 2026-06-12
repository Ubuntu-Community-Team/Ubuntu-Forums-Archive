---
title: "unload desktop from memory?"
date: 2007-05-10
forum: General Help
---

### Post by lefnire on 2007-05-10
I'm running ubuntu server (aka, terminal). I don't need a desktop, but every once in a while i use programs that requires x windows (ntfs-config, eclipse, etc). I have 3 questions:
1) can I run these graphical programs without having a desktop gui? In other words, can I run off terminal until I run one of these programs, then be switched to that program's graphical environment? if so, how?
2) can I run a desktop (xfce or icewm) that will not be automatically loaded, but can be manually loaded from the terminal until I'm done doing my thing, and then unloaded from memory? if so, how?
3) when I switch between terminal and desktop in regular ol' ubuntuu-desktop by hitting alt+f1 (for terminal) and alt+f7 (for desktop), does hitting alt+f1 remove the desktop from memory, or just run it in the background until I hit alt+f7 again?

---

### Post by Jussi Kukkonen on 2007-05-10
> 1) can I run these graphical programs without having a desktop gui? In other words, can I run off terminal until I run one of these programs, then be switched to that program's graphical environment? if so, how?
You will need to have X running when you run a graphical program. Starting X can be quite fast, so there's no need to keep it running all the time if the memory use is a problem.

> 
2) can I run a desktop (xfce or icewm) that will not be automatically loaded, but can be manually loaded from the terminal until I'm done doing my thing, and then unloaded from memory? if so, how?
A desktop environment or a window manager, sure. When you have installed the wm you like, first prevent it from loading on startup (with gnome you can e.g. rename /etc/rc2.d/S13gdm  to /etc/rc2.d/K87gdm, so gdm won't start). You can start it later with **startx** or if you want to go through gdm with */etc/init.d/gdm start*.

I assume just installing a wm without a desktop environment will probably give you this effect (no autologin) out of the box.
> 
3) when I switch between terminal and desktop in regular ol' ubuntuu-desktop by hitting alt+f1 (for terminal) and alt+f7 (for desktop), does hitting alt+f1 remove the desktop from memory, or just run it in the background until I hit alt+f7 again?
Everything is still running.

By the way, if you have a desktop machine, the easiest way to run some random GUI apps on the server is to ssh from desktop to server and start the program (it'll use the X server on the desktop). You'll need to edit sshd_config to allow this and use -x option in shh.

---

