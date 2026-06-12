---
title: "Close programs"
date: 2007-05-06
forum: General Help
---

### Post by midlandman on 2007-05-06
Hi.
Can someone tell me how to close out a program that crashes, like ctrl-alt-delete in windows? For some reason I can't get frostwire to close.
Thanks.

---

### Post by navneeth on 2007-05-06
Usually, when a program doesn't close the first time, pressing the exit button the second time should bring up the "Force Quit" button dialog. That should close the program. 

Or you could go to the System Monitor - The "Task Manager" of GNOME(I think you find it under System->Preferences), go to the Process tab, right click on the program's process and click 'End Process'.

If you have Automatix installed, you could install <something>(I don't know the exact word for it) which will let you access the systme monitor via Ctrl+Alt+Del.

---

### Post by raja on 2007-05-06
You can add an applet to the panel called force quit, which you can use. Usually you can force this by just clicking the window close button. For unresponsive applications, you can also kill the application from a terminal with the command 'killall'.

---

### Post by midlandman on 2007-05-06
Thanks guys. I might have to go the Automatix route, because sometimes at YouTube it'll freeze and I don't have access to my desktop. That's why I need something like ctrl-alt-del.
Thanks again!

---

### Post by raja on 2007-05-06
I think it is overkill installing Automatix just for this. Remember that Automatix has its own problems and is better avoided. 
All you have to do is open gconf-editor and in /apps/metacity/key-binding commands, set a command to gnome-system-monitor. Then you map that command to Ctrl-Alt-Del key. 
It is easier doing it than it sounds.

---

### Post by frup on 2007-05-06
I think the important thing is to find out why frostwire isn't closing properly, it's happening to me too. I know these sorts of programs like to stay open as much as possible and usually click the X sends it to the tray, but for me there is no icon in the system tray either, and there seems to be no option to close it without going to the tray and so force quit seems to be the only option.

---

### Post by notwen on 2007-05-06
If you're wanting a list of all running processes and the [Kill] button that you may have gotten use to in Windoze.  Try System--->Admin--->System Monitor   --- from here click on the Processes tab, select whats locked up and kill it using the button located conveniently below the list of running processes. Hope this helps. =]

---

