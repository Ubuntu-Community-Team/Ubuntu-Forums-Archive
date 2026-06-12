---
title: "No text console"
date: 2007-03-29
forum: General Help
---

### Post by koma77 on 2007-03-29
Hi,

Today I tried to switch from Gnome to a text console by pressing Ctrl + Alt + 1 as usual.

But instead of a text console I get just garbage on the screen...

I can switch back to X again with no problem.

It has worked perfectly before. Is it a bug? What can I do?

/Magnus

---

### Post by acormack on 2007-03-30
If you reboot does the problem go away?

---

### Post by koma77 on 2007-03-30
No, it's the same thing on every boot.

The graphics garbage on the screen is different from time to time though.

I think this is a bug... Should I report it in Launchpad?

---

### Post by acormack on 2007-03-30
If it only just started today I think you should try to think about what changed on your machine today.

Did you add any new software or change any settings.

If you create a new user, reboot  and log on as them does it work then?

---

### Post by koma77 on 2007-03-31
I don't use the text console every day, so I don't know exactly when it started...

It may have started when I installed beryl?

---

### Post by taurus on 2007-03-31
Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and add this one to the end of the line of your kernel entry.

```
vga=773
```
Reboot.  Now, see if you can get to one of the consoles?

---

### Post by acormack on 2007-03-31
If you create a new user, reboot and log on as them does it work then?

sudo useradd fred -p fredpass

---

### Post by stylishpants on 2007-03-31
> **koma77 said:**
> Hi,

Today I tried to switch from Gnome to a text console by pressing Ctrl + Alt + 1 as usual.




Just so we are clear here -- you actually are doing Ctrl + Alt + F1, right?  

Ctrl + Alt + 1 is something completely different.

---

### Post by Prometheum on 2007-04-01
I have a similar problem. For a while now, for no apparent reason, I have not been able to see any of my text consoles (from tty1-6). I'll hit ctrl+alt+f1 and my screen will go entirely black. However, if I type in my username and password into the blank screen, hit ctrl+alt+f7 and hit the w command, I can see myself logged in on tty1. If I chmod -x to gnome, then I can reboot and use consoles, but otherwise I can't. If I chmod +x back to gnome and start it, then all my consoles will disappear. 

What could this be caused by? I am utterly baffled.

---

