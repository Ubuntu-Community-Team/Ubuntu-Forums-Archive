---
title: "not booting"
date: 2013-01-25
forum: General Help
---

### Post by ourgranville on 2013-01-25
I need help, my wifes Dell inspiron mini note book updated its version of ubuntu last night & ran fine . when it can to booting today though all i get is black screen & 2 lines of text..1) Enabling additional executable binary formats binfmt- support & 2) checking battery state...
On the right of the screen each line has [ok]
i have tried what little i know but no change , i am very ignorent when it comes to this level of problem , any suggestions please

---

### Post by kc1di on 2013-01-25
does it show a grub menu of just the blank screen?

Sounds like grub may have gotten corrupted some how. 

you may want to try boot-repair [here.]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by ourgranville on 2013-01-25
Thanks Dave, but i don't what a grub  menu is but nothing else is showing , but i will try you link.
Thanks
Robbie

---

### Post by kc1di on 2013-01-25
> **ourgranville said:**
> Thanks Dave, but i don't what a grub  menu is but nothing else is showing , but i will try you link.
Thanks
Robbie

hi Robbie,
the Grub menu is the menu that should come up when you boot that gives you the option of selecting the O.S. To boot.

Let me know how you make out.

---

### Post by ourgranville on 2013-01-26
i get the Dell screen & F key options for boot choice or set up ...then as said before. wondering if its the net book hardware

---

### Post by steeldriver on 2013-01-26
It sounds to me like it's booting, but failing to start the graphical desktop

Often that's a problem with graphics drivers - e.g. when you have installed a proprietary driver and then a subsequent kernel upgrade is incompatible with it

Can you switch to / login in at one of the virtual terminals (Ctrl-Alt-F1 or Ctrl-Alt-F2 etc.)?

---

### Post by ourgranville on 2013-01-26
> **steeldriver said:**
> It sounds to me like it's booting, but failing to start the graphical desktop
 
Often that's a problem with graphics drivers - e.g. when you have installed a proprietary driver and then a subsequent kernel upgrade is incompatible with it
 
Can you switch to / login in at one of the virtual terminals (Ctrl-Alt-F1 or Ctrl-Alt-F2 etc.)?
 
 
 
no ..tried every way to access something

---

