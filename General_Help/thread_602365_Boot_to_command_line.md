---
title: "Boot to command line"
date: 2007-11-04
forum: General Help
---

### Post by PhiSI on 2007-11-04
Hi all
How can I tell ubuntu (or xubuntu here) to boot into a command line environment and not to a graphical desktop. I just installed 7.10 xubuntu on my old PC. Now I want to use it as "home server". Since it is really old it uses 10% cpu just for the desktop (even with all effects turned off). So I#m trying to boot it to the command line. What is the best way to do so? Alter grub.conf or the graphical login (don't know which one is in use)?
My ultimate goal would be a bootmenu where I can choose either desktop mode (with usual xfce etc..) or server mode (only command line + start apache, mysql, etc + optionally start x .. do smth. .. drop back to console)

---

### Post by p_quarles on 2007-11-04
This is an unusual (and therefore interesting in my view) request. I thought it would be simple to find the answer, but there's not a lot out there. I ended up fiddling with a virtual machine for a bit, and got something that should work for you.

In fact, it is pretty simple. All you have to do is edit the default DM:
```
sudo nano /etc/X11/default-display-manager
```
Simply comment out the one line in that file (I'm not sure what it will be in Xfce, but whatever it is, make a note of it). By default, the display manager script in /etc/init.d has the "HEED_DEFAULT_DISPLAY_MANAGER" setting on "true." By commenting out the line, you've disabled any default display manager, and the system will boot straight to the terminal. 

Now, to get the graphical environment, all you need to do is invoke the display manager from the command line. For Gnome, it would be:
```
sudo gdm
```
You'll just need to replace "gdm" with whatever the display manager actually is for Xubuntu. 

Anyway, I tried this, and it does work. That said, there may be better ways, so you may want to stick around and see if anyone else replies.

---

