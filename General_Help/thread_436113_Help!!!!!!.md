---
title: "Help!!!!!!"
date: 2007-05-07
forum: General Help
---

### Post by Sockerdrickan on 2007-05-07
I'm getting really mad everytime a fullscreen app HANGS my pc and I have to restart X.org ( canceling the FireFox downloads)

HOW DO I FREAKIN' KILL<-- the current fullscreen app? :popcorn:

---

### Post by FluffyElmo on 2007-05-07
*Ctrl-Alt-F2* will open a new text terminal window where you can log in and kill the process. Alternately, try *Ctrl-Alt+(the right or left arrow key)* to move between virtual desktops. Or *Alt+f2* may let you run gnome-terminal and kill the process from there. It depends on how badly your application is locking up...

---

### Post by FluffyElmo on 2007-05-07
*ps-eaf |grep programname* will list the processes, where programname is part of the name of the executable. The left number is your process id. Then *kill processid* should kill the application. If that can't kill the process then *kill -9 processid* should.

---

### Post by Sockerdrickan on 2007-05-07
Thanks, will try.

---

### Post by Sockerdrickan on 2007-05-07
ALT+F2 don't work
ps-eaf |grep programname returns ps-eaf not found

---

### Post by aidanr on 2007-05-07
it's ps -eaf eg.
```
ps -eaf|grep firefox
```

---

### Post by FluffyElmo on 2007-05-07
Sorry, there was supposed to be a space between ps and -eaf...

---

### Post by Sockerdrickan on 2007-05-07
ps -e |grep zsnes
kill 5881

instant win

---

### Post by Sockerdrickan on 2007-05-07
Can I somehow change the other "fullscreen terminals" (whats the name) to 1440x900?

---

### Post by cmost on 2007-05-07
I have never understood why Gnome doesn't have something like CTRL+ALT+ESC, like KDE, which changes the mouse cursor to a skull & crossbones and allows one to kill any application you click on next.  I used to be a die-hard KDE user but have been content with Gnome since switching to Ubuntu over a year ago.  To me, Gnome looks much more professional than KDE.  It's the lack of certain KDE niceties like the one mentioned above, however, that always makes me consider doing a sudo apt-get install KDE-desktop!!!

---

### Post by Sockerdrickan on 2007-05-07
Can I somehow paste a url from the GUI in TTY7 to TTY2 ? (Will use it in wget)

---

### Post by rich.bradshaw on 2007-05-07
Right click on top panel/add applet, choose the force quit one. 

Click on that , and any window you click on next it force quits. Best GNOME applet ever!

---

### Post by Sockerdrickan on 2007-05-07
> **rich.bradshaw said:**
> Right click on top panel/add applet, choose the force quit one. 

Click on that , and any window you click on next it force quits. Best GNOME applet ever!
Yes that's a good choice for non-fullscreen apps ;)

---

