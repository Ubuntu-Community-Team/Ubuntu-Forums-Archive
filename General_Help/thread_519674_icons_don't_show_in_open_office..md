---
title: "icons don't show in open office."
date: 2007-08-07
forum: General Help
---

### Post by Jamesbowden on 2007-08-07
I think this may be the first time I have used open office since I reinstalled 7.04, but I opened it today and noticed that all the icons for the menu bar (like the save disk, the open folder etc.)

does anyone know how I can get these back?

(screen shot attached)

---

### Post by stchman on 2007-08-07
> **Jamesbowden said:**
> I think this may be the first time I have used open office since I reinstalled 7.04, but I opened it today and noticed that all the icons for the menu bar (like the save disk, the open folder etc.)

does anyone know how I can get these back?

(screen shot attached)

It is in the Tools--->Options---View I believe.  Start there.

---

### Post by krrh on 2007-08-07
I had the same problem and was able to fix it by changing the icon size from automatic to either small or large.  I believe I also changed the icon theme, after which the OpenOffice tool bars appeared normally.

These settings are availabe in the Options, as noted above.

---

### Post by Irony on 2007-08-07
Go to your home directory press Ctrl H (to view hidden folders) and delete the openoffice directory (make a copy of it first) - then start openoffice.

---

### Post by FuturePilot on 2007-08-07
What icon theme are you using? I had this problem only when I used the Tango icons. [http://ubuntuforums.org/showthread.php?t=415797]("http://ubuntuforums.org/showthread.php?t=415797")Solution was to do this
```
sudo apt-get install openoffice.org-style-tango
```
Or go Tools>Options>View and change the icon theme to Human and see if that works.

---

### Post by Jamesbowden on 2007-08-07
> **FuturePilot said:**
> What icon theme are you using? I had this problem only when I used the Tango icons. [http://ubuntuforums.org/showthread.php?t=415797]("http://ubuntuforums.org/showthread.php?t=415797")Solution was to do this
```
sudo apt-get install openoffice.org-style-tango
```
Or go Tools>Options>View and change the icon theme to Human and see if that works.

Yes I was using tango, and yes that was the solution, thanks

---

### Post by RedSquirrel on 2007-08-07
Tango is not the only theme, of course... ;)

$ apt-cache search openoffice.org-style
openoffice.org-style-andromeda - Default symbol style for OpenOffice.org
openoffice.org-style-crystal - Crystal symbol style for OpenOffice.org
openoffice.org-style-default - Default symbol style for OpenOffice.org
openoffice.org-style-human - Human symbol style for OpenOffice.org
openoffice.org-style-industrial - Industrial symbol style for OpenOffice.org
openoffice.org-style-tango - Tango symbol style for OpenOffice.org
openoffice.org-style-hicontrast - Hicontrast symbol style for OpenOffice.org

---

### Post by kiev on 2007-08-10
Open Office - icon not show (gutsy)

[IMG]http://www.web-standart.net/tmp/openoffice-gluk.png[/IMG]

icons are shown only under and cursor, disappear then
Please help!

---

### Post by RedSquirrel on 2007-08-11
> **kiev said:**
> Open Office - icon not show (gutsy)

icons are shown only under and cursor, disappear then
Please help!
I haven't seen that problem before, but it just sounds like a bug. gutsy is still in development, so one can't expect it to be totally functional yet. 

Here is a bug that sounds similar (there may be others):

[https://bugs.launchpad.net/ubuntu/+bug/34909](https://bugs.launchpad.net/ubuntu/+bug/34909)


EDIT:

If you can't find a reasonable solution, you might want to consider installing OpenOffice from its own website rather than using the one from the Ubuntu repositories. I haven't had to do that myself, but it's another possibility.

EDIT #2:

[https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/36256](https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/36256)

It seems this is (or was) an issue that can occur if people install GNOME and KDE or Xfce. 

In your case, it might still have something to do with the fact that gutsy is still in development though (and months away from being officially released).

---

### Post by kiev on 2007-08-12
Thanks You! I installing openoffice.org-kde and solves the problem.
Only now scrolling works through the wheel of mouse, and by a cursor it is not.

---

### Post by BobSongs on 2007-08-14
[FONT=Verdana]I noted the same problem with OpenOffice.org in Feisty. No icons. The initial solution:
[/FONT][INDENT][FONT=Verdana]**Tools -> Options.**
[/FONT][/INDENT][FONT=Verdana]Under "OpenOffice.org" click **"View"**.

Under **"Icon size and style"**: Left button: **"Small"**, right button: **"Human"** (the 2nd Human as my copy seems to have two in the list).

The more pleasing solution was indeed to install more icon themes through Synaptic as previously pointed out in this thread.
[/FONT]

---

### Post by Dfects on 2007-08-16
> **BobSongs said:**
> [FONT=Verdana]I noted the same problem with OpenOffice.org in Feisty. No icons. The initial solution:
[/FONT][INDENT][FONT=Verdana]**Tools -> Options.**
[/FONT][/INDENT][FONT=Verdana]Under "OpenOffice.org" click **"View"**.

Under **"Icon size and style"**: Left button: **"Small"**, right button: **"Human"** (the 2nd Human as my copy seems to have two in the list).

The more pleasing solution was indeed to install more icon themes through Synaptic as previously pointed out in this thread.
[/FONT]

THANK YOU! :)

---

