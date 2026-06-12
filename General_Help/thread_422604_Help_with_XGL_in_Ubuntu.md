---
title: "Help with XGL in Ubuntu"
date: 2007-04-25
forum: General Help
---

### Post by mikedragon on 2007-04-25
Hi! I used Poofyhairguy's guide how-to install Xgl in Ubuntu. At the end, I wrote 'thefuture' in terminal, and i noticed that the shadows appeared, and terminal make transparent and other details changed. I've started being happy, but what happened when I press CTRL+ALT+<or> or F12 or anything else? Nothing . I don't know why, I've got NVidia GeForce 5500 FX. Could you help me, please? 

With regards.
mikedragon

---

### Post by mikedragon on 2007-04-25
Please help me, I'm still waiting for answer! I don't have much time. Thx

---

### Post by NullHead on 2007-04-25
Please explain more about your problem...one can only help if he knows whats wrong;)

---

### Post by mikedragon on 2007-04-29
I mean in xgl don't works 3D desktop as a cube. Look at this right down corner of this screenshot:
[img]http://img105.imageshack.us/img105/4995/zrzutekranuxj8.jpg[/img]

But some things in xgl works like shadows, transparency. What do you think?

---

### Post by NullHead on 2007-04-29
Run and try this in a terminal.
```
sudo apt-get install gnome-compiz-manager

```
Then run it by typing this 
```
gnome-compiz-preferences
```
Then switch to the workspaces tab and change the number of viewports and that should do it...but i found i have to run that program everytime i start the computer or logout. So I use beryl and you can get that by typing  in ```
sudo apt-get install beryl
```

---

### Post by mikedragon on 2007-04-30
Thank you NullHead! It works! I so glad :) Problem resolved

---

### Post by NullHead on 2007-04-30
> **mikedragon said:**
> Thank you NullHead! It works! I so glad :) Problem resolved
Any time :)
did you end up using beryl or gnome-compiz-preferences??

---

### Post by mikedragon on 2007-04-30
> **NullHead said:**
> Any time :)
did you end up using beryl or **gnome-compiz-preferences**??

:) If you can, please help me in this topic:
[http://ubuntuforums.org/showthread.php?t=428207](http://ubuntuforums.org/showthread.php?t=428207)

---

