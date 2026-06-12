---
title: "[SOLVED] Installing a .bin"
date: 2007-08-25
forum: General Help
---

### Post by Het Irv on 2007-08-25
Found a Sub game with a .bin installer.  Ran installer in terminal w/ sudo.  The installer created a "desktop configuration file" on my desktop that does nothing when clicked.  I even tried clicking the file in Nautilus and still nothing.  There is no other evidence that the .bin file did anything other then the file on the desktop.  What's the next step.

---

### Post by ruibernardo on 2007-08-25
Try running the game from the terminal (menu Applications, Accessories, Terminal) and check what errors it gives when you execute it.

---

### Post by Het Irv on 2007-08-28
I'm not sure what you wanted me to run but this is the file that is on the desktop.  I tried twice to run the program by dragging the file into the terminal and then repeated the attempt with sudo.

```
grail@grail-desktop:~$ '/home/grail/Desktop/Danger from the Deep.desktop' 
bash: /home/grail/Desktop/Danger from the Deep.desktop: Permission denied
grail@grail-desktop:~$ sudo '/home/grail/Desktop/Danger from the Deep.desktop' 
Password:
sudo: /home/grail/Desktop/Danger from the Deep.desktop: command not found

```

This is copied straight from the terminal.  What now?

---

### Post by ruibernardo on 2007-08-28
When I said "*Try running the game from the terminal*" it was to try to run the called application from the menu. Check what application is called from the menu by editing the menu (right click on "Applications" menu) and look the applications name, then type the name of the application (path included if needed) on the terminal and look for the errors it dumps.

Usually for games you need the graphic card drivers. You can enable them from the "Restricted Controllers Manager" in the menu System, Administration menu.

---

### Post by Het Irv on 2007-08-28
Sorry, (see Signature)  This might be the root of my problem.  There is no menu item for the game.  The .desktop file was the only thing that appeared after I ran the .bin installer.

---

### Post by VitaminG on 2007-08-28
actually, he's talking about the game itself, not any shortcuts to it. right click on the .desktop file and go to the Launcher tab. check what it says in the "Command" field. now open the terminal and copy that line into the terminal. then run it and copy the output to here.

---

### Post by Het Irv on 2007-08-28
```
grail@grail-desktop:~$ dangerdeep
dangerdeep: error while loading shared libraries: libfftw3f.so.3: cannot open shared object file: No such file or directory

```

---

### Post by ruibernardo on 2007-08-28
Look into that .desktop file:

```
 cat Deep.desktop
```

Search for something beginning with /usr/local/... and try to execute it.

Sorry, although I've played this game, I don't have it installed now, and I can't be more precise about the full path of the game.

---

### Post by Het Irv on 2007-08-28
is that the full code?  I got a no such file or Directory error.

On a side note, is the game any good?

---

### Post by ruibernardo on 2007-08-28
Yes, the game is good, it's like "Silent Hunter 2". Please check this thread about your problem:  [Danger From the Deep -- Permissions?]("http://ubuntuforums.org/showthread.php?p=3201352")

---

### Post by Het Irv on 2007-08-28
W00T! Game is up and running.  I had the same problem as   	
cogadh.

---

