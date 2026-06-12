---
title: "Help"
date: 2008-03-15
forum: General Help
---

### Post by lilalmond on 2008-03-15
Hey

i have a problem...
I was trying to make the animations effect from compiz fusion to work but it doesnt...
Anyway i was in the desktop effect/cuztomization categorie reading some thread about it,and i typed compiz in a terminal since then my puter screwed up and im just able to use this window from the forum...
My terminal is minimized and cant maximize it or close it
I also lost my top bar from the window
I tried to alt+F2 to type in reboot but i cant even do it
Any help would be welcome before i reboot manually using the start button
Thx

---

### Post by sisco311 on 2008-03-15
Ctrl+Alt Backspace to restart the X server
or
Ctrl+Alt F1 to login in text mode and reboot the computer from the command line.

---

### Post by chewearn on 2008-03-15
ALT+F2, type:
```
metacity --replace
```

This will kill compiz, and enable metacity, which is the basic gnome window manager, and bring back the window titles and borders.

---

### Post by lilalmond on 2008-03-15
i cant alt+F2
i did ctrl+alt+backspace  my puter rebooted and now its all screwed up...
I cant do anything since my window bar disapeared
I also lost my 4 desktop
i dont even have the window list on my bottom panel even tho i right clicked on the bottom panel to *** "window list"
i cant acces terminal or alt+F2
basically all i can do is reboot manually using the start button or ctrl+alt+backspace, but i just did that and my puter is all screwed up
this sux...

---

### Post by lilalmond on 2008-03-15
By the way i also lost my top panel bar 
i just have this window from the forum on the srceen but cant close or minimize since i lost my window boarder...

---

### Post by sisco311 on 2008-03-15
press Ctrl+Alt F1 and login in text mode
edit your compiz settings:
(nano is a text editor)
```
nano ~/.config/compiz/compizconfig/Default.ini
```delete *animation* from the line [B][I]'as_active_plugins = ...'
[/I][/B]save the file and exit(Ctrl+o, Enter, Ctrl+x)

go back to the gui and restart the x server(Ctrl+Alt F7, Ctrl+Alt Backspace)

Or you can delete the config files from the text mode. Next time you start your gui compiz will recreate the files with default settings.(NOTE: You will lose all your compiz settings)

```
rm -fr ~/.config/compiz/
```

---

