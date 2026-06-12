---
title: "How to find the commands and options that correspond with clicking an icon in Unity?"
date: 2014-09-21
forum: General Help
---

### Post by Sjaak Adriaanse on 2014-09-21
Hi all,

I run 14.04 and I am now experimenting with Fluxbox. To use Fluxbox you have to edit configuration files, so you have to know the commands, including options, that are executed when you would start a program in Unity by f.i. clicking on an icon in the Dash or the  toolbar. Most programs seem to be located in /usr/bin, so looking there can help (f.i. Firefox is /usr/bin/firefox) 
Is there a general way to find the commands and options that correspond with clicking an icon in Unity?

---

### Post by deadflowr on 2014-09-21
The files for the launchers are located in /usr/share/applications.
These are .desktop files, simply clicking on them won't open them, so best is to open them from within a text editor like gedit.
The commands are the Exec= part.

I should also point out that unity uses a feature known as quicklist.
Those are the options you get when right-clicking on the launcher icon.
These fall under the Actions section of the .desktop file.
These are usually toward the end area of the file.
They tend to have the action name, and the action's command(Exec)

I tend to open gedit, then click on the fat Open button on top bar-area, then scroll to Computer, then go to usr, then share, then applications.
The find the desktop file, hopefully I want, and open it.

Hope something here helps...

---

### Post by CantankRus on 2014-09-21
Another way is to run gnome-system-monitor and enable "Command Line" in preferences
where you can see the command that started a process.

Also to add to **deadflowr's** comment, you can drag a launcher from /usr/share/applications
into an open gedit window to view.

---

### Post by Sjaak Adriaanse on 2014-09-22
Thanks! This is exactly what I was looking for! I will mark this thread 'Solved'

Greetings,
Sjaak

---

