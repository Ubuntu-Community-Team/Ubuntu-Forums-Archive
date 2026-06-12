---
title: "Gutsy problem with Vista"
date: 2007-10-20
forum: General Help
---

### Post by Daryl7931 on 2007-10-20
I upgraded from Feisty to Gutsy yesterday, and when I restarted, Vista was missing from my boot menu.  I booted from the Vista Reinstallation disk and fixed the Master Boot Record, but now Ubuntu is missing from the boot menu, and Vista just loads automatically.  How can I fix this without reinstalling Ubuntu?

---

### Post by Daryl7931 on 2007-10-20
Anyone?

---

### Post by Eric the Grey on 2007-10-20
Here is a How-To for exactly that:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I've had to do this a few times... :-\"


:cool: Eric the Grey

---

### Post by Daryl7931 on 2007-10-21
Another problem, now.  I tried the information at Eric the Grey's link, and it worked, but now I'm back to my original problem;  The Grub loads, and I can boot to Ubuntu, but the Vista option is not there.  

Also, why are there 2 Ubuntu options and 2 Ubuntu recovery options?  I've tried both, but they go to the same thing.

---

### Post by ceno-byte on 2007-10-21
hey Daryl7931 i found some information that might be useful to you it is right from ubuntuguide.org

 How to add Windows entry into GRUB menu

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
```
gksudo gedit /boot/grub/menu.lst
```

Append the following lines at the end of file

title		Microsoft Windows
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

Save the edited file

Try that and post back

as to why you have 2 ubuntu options and 2 possible ubuntu revcovery options my best guess is that you have 2 kernals installed.

---

### Post by Daryl7931 on 2007-10-21
I tried that, and it showed up as an option, but selecting it just brought up some Windows Memory Diagnostics tool.  

Cool site, though, I'll go see if I can find anything.

---

### Post by Daryl7931 on 2007-10-21
Update:  Problem solved;  I used your methed, only I made 3 additional Windows ones, with the numbers 1, 2, and 3 replacing 0 (But not hd0), and the second one booted Vista.  I'll delete the extras now, thanks!

---

