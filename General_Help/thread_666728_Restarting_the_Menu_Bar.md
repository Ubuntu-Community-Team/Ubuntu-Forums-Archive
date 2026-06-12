---
title: "Restarting the Menu Bar"
date: 2008-01-13
forum: General Help
---

### Post by bbrownderville on 2008-01-13
Ok So i am completely new to linux and i have somehow removed my menubar from my desktop and i have no clue how to get it back.  I am useless without it. can somebody tell me how to get it back please. thanks..

---

### Post by Omnios on 2008-01-13
K there is the menu and the menu bar.
 
The menu items can be beadded by right clicking the bar and choosing add stuff from a list.
 
As fo the hole bar on the top right click the bottom and add bar and choose to have it put on the top.
 
then you can right klick it and add stuff.

---

### Post by bbrownderville on 2008-01-13
There are no bars at all on my desktop.  The only thing i have is icons.  I somehow pushed some wrong key combination and removed both menu bars.  I have no clue how i did this.  Please help..

---

### Post by bbrownderville on 2008-01-13
i dont know if it is possible but could i have shut down gnome? i am totally clueless at this point.

---

### Post by Omnios on 2008-01-13
ctr-alt backspace will restart xserver and boot to the log on screen. 
 
 Also think there is a terminal command to start the bars.

---

### Post by Tenken on 2008-01-13
To turn the bars back on with restarting X you can hit Alt+F2 and type

```
gnome-panel
```

---

### Post by bbrownderville on 2008-01-13
> **Tenken said:**
> To turn the bars back on with restarting X you can hit Alt+F2 and type

```
gnome-panel
```

I tried that and it didnt work.  I have completely restarted my computer three times and nothing happened.

---

### Post by Tenken on 2008-01-13
After you run that command, try this in a terminal (hit alt+F2 again, and type gnome-terminal to open the terminal).

```
ps -A | grep gnome
```

If you see gnome-panel that means that the program is running,if it is try hovering your mouse near the top and bottom, maybe the bars became "hidden".

---

