---
title: "ubuntu freezes after login.."
date: 2008-06-24
forum: General Help
---

### Post by SimonTheMime on 2008-06-24
Hey. I've installed ubuntu on my sis' widescreen laptop a few days ago, and I was doing the last of some eyecandy customization.. I tried to change the usplash([this one](http://gnome-look.org/content/show.php/Hardy-Colors+Usplash?content=79631)), restarted to see if it worked, but now when I log in (on fresh restart), the desktop shows up, panels, my conky on the background, but everything's frozen.

I can make blue boxes on the desktop by dragging the cursos, and I can right click. But all other functionality is lost. Conky updates, and I've also tried killing it in tty4 to see if that was it, but the screen remains frozen. Compiz still works, I can change workspace, but the workspace applet is frozen and shows me as being on the same workspace. None of the applets/applications on the panels can be selected, and it can not be moved either.

When I restart x, the problem gets even worse, where the whole thing just turns black, and the cursor remains an X. Please help!! Thanks in advance

---

### Post by spiderbatdad on 2008-06-24
Not enough information to get good help.
Please post some system specs, including video card:```
lspci
```

Also dmesg might be helpful:```
dmesg > ~/Desktop/dmesg.txt
```right click the file it writes and select "create an archive" upload the archive here with the "manage attachment" tool below. Also post the out put of lspci via copy/paste.

---

### Post by SimonTheMime on 2008-06-24
It's integrated intel, on an inspiron 1720.

I can't copy-paste or save to desktop any of it because all that functionality is frozen. It works sporadically sometimes for a few seconds, and then it's messed up again. It loads up slowly after logging in, around 5 seconds of blackness. Top panel shows, some applets go missing, conky shows with full desktop. I can do all the compiz stuff, and switch desktops, I can turn it on and off as a WM, but everything's still messed.

 It was working fine until this restart.Is there a command to edit the startup programs?

---

### Post by spiderbatdad on 2008-06-24
how about failsafe gnome from the options menu at the login screen?

---

### Post by SimonTheMime on 2008-06-24
Yeha that works.

---

### Post by SimonTheMime on 2008-06-25
What should I do from here?

---

