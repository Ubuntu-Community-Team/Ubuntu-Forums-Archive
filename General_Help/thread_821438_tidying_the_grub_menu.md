---
title: "tidying the grub menu?"
date: 2008-06-07
forum: General Help
---

### Post by ww711 on 2008-06-07
How to tidy the grub menu?

At the moment on my dual boot laptop, there are lots of older kernels that are listed on the grub menu, I'd like to remove some of them.

---

### Post by sandysandy on 2008-06-07
u can edit ur menu.lst file

code [COLOR="Blue"]gksudo gedit /boot/grub/menu.lst[/COLOR]

regards

---

### Post by ww711 on 2008-06-07
great, thanks for that.

---

### Post by forger on 2008-06-07
menu system > administration > synaptic package manager

on the lower left corner, click "**status**"
select "**Installed (local or obsolete)**"
select the packages that start with "linux-" and right-click on them and choose "Complete removal"
click "Apply"
this should clear up the obsolete ones

you can also clear up the "not installed (residual config)" category, those are packages that you've removed and have stayed in your system.

now select the "Installed" category, click Search, select "Name" (not "description and name") and type: **linux-**
it should provide you with all the packages that contain linux- in their name

Find the ones you wish to remove, but I suggest to  **at least don't remove the 3 latest** kernels

---

### Post by drs305 on 2008-06-07
It's best to let StartUp-Manager do the work for you to prevent errors. If you want to edit menu.lst, there are instructions for that as well.

Here is a pretty comprehensive HOWTO on the grub menu and startupmanager:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

