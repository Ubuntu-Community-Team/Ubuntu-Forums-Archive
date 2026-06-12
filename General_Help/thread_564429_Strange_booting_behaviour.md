---
title: "Strange booting behaviour"
date: 2007-10-01
forum: General Help
---

### Post by hevymetldude on 2007-10-01
Ok let me explain this.
I have 7.04 "running" on my DELL Dimension 8300.
IF it boots - it runs perfectly.

When I start my computer it usualy needs 20 - 30 restarts to finally come to a console or even better the GUI.
Sometimes it just works the first time as expected, but generally its like

DELL Startup-Screen
GRUB
reboot
DELL Startup-Screen
GRUB
reboot
DELL Startup-Screen
GRUB
reboot
DELL Startup-Screen
GRUB
reboot
and so on.

Where can I find whats going on - what is causing the crash ?

There is no difference between a "cold start" and a simple reboot.. It behaves as described on unpredictable occasions.

Any Ideas ?

---

### Post by ramjet_1953 on 2007-10-01
Have you tried booting in terminal mode?
This is usually the second choice in the GRUB menu.

This will let you see any errors that are occurring.

Regards,
Roger :cool:

---

### Post by anaconda on 2007-10-01
Might also be hardware realted error.

My old machine did that when its power was failing.

You can test  it.  Does it work better if you disconnect everything you can. (to reduce load)

---

### Post by hevymetldude on 2007-10-02
I allready tried rebooting in terminal mode...same thing happening...
I see some messages about setting up PCI and then it crashes.

I'll try to disconnect some devices and tell you.

---

### Post by AuToFiRE on 2007-10-02
I had this exact same problem

when it says loading grub press esc

then edit the first option. goto the second line, edit, and remove quiet splash from the end of it. press enter then press b let it load, log in and edit the boot file (im too tired right now to remember what it is) and remove the quiet splash from it and save, that should solve the problem


EDIT: ok i remember now, its  /boot/grub/menu.lst

if you dont know how to edit files, use this, it saved em a few times too

                                             gksudo nautilus

---

### Post by hevymetldude on 2007-10-15
ok - I disconnected all my USB-devices and the problem still exists.

I'll try AuToFiRE solution tonight.

---

