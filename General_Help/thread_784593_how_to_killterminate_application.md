---
title: "how to kill/terminate application"
date: 2008-05-06
forum: General Help
---

### Post by verby on 2008-05-06
in kde I could press ctrl+esc and it opened box which showed me which application is running, also could kill any apps from there.
Is there anything like this in ubuntu?

---

### Post by ejay563 on 2008-05-06
if you just want to kill a program, you can just hit alt+F2, type pkill [programname] and push run, and that'll usually take care of it. If you don't know the "real" name of the application (by real, i mean what you would type at a command prompt to launch the program), then open a terminal, type ps -a, and look through the running programs until you find the one you want to kill, take note of the process id number, then type kill [pid]. You might be able to kill processes from the system monitor (System>(settings or something)>system monitor).

---

### Post by knutschr on 2008-05-06
> **verby said:**
> in kde I could press ctrl+esc and it opened box which showed me which application is running, also could kill any apps from there.
Is there anything like this in ubuntu?

You can start systemmonitor.
In the tab processes you will see what is running, and kill what you want from there.
(I have allways this program running in one of my desktops).

---

### Post by abbot on 2008-05-06
There is also a Force Quit icon that you can add to a toolbar.  If you'd rather do it with just a few clicks rather than opening a program, sometimes I do that.  You just add it to your toolbar with a couple clicks then when you click on the icon and click on the frozen window it will kill the program.

---

