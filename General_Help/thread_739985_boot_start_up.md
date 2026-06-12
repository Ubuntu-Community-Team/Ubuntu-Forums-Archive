---
title: "boot start up"
date: 2008-03-30
forum: General Help
---

### Post by jesse c on 2008-03-30
i have noticed that if i let the boot page auto start after its 20sec. timer, the start page is so big that the task bar is off the screen.At first i thought it was just a blank brown screen but when i  moused past the edge the task bar shows up so i can shut down and restart from boot.Now if i hit the enter key before the 20sec. everything is normal. Does anyone have a solution so i can just power up my system,walk away,and come back to a "normal" screen?
thanks jesse c

---

### Post by danwood76 on 2008-03-30
It might be that grub is booting ubuntu up with some funny options.

could you post your menu.lst please?

```

cat /boot/grub/menu.lst

```

---

### Post by jesse c on 2008-04-20
SOLVED after missing my 15sec. start up window once again and having it boot to a blank brown screen i started messing around with the keyboard and happened across the feature where you hit the "window" key and roll the mouse wheel which is a zoom feature i didnt know about.Once i zoomed out everything fit on the screen,so i turned off the computer and rebooted to see what would happen and sure enough it stayed zoomed out.Easy fix,PROBLEM SOLVED

---

