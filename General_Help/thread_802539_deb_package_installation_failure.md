---
title: "deb package installation failure"
date: 2008-05-21
forum: General Help
---

### Post by Nubnut on 2008-05-21
I downloaded and the deb package for "eXe eLearning HTML Editor" from [http://exelearning.org/](http://exelearning.org/), I used the graphical installed on Edubuntu 8.04(clicked package and Package Installer started and finished without errors) but recieve the following error when I run the application from the applications menu,-

Could not launch menu item, Failed to execute child process "exe" (No such file or directory)

I normally install application using Synaptic so am unused to installing deb packages,
Is eXe included in any of the Synaptic Repositories?
Can anyone help?

---

### Post by rocky5051 on 2008-05-21
I don't have the program installed itself but here's an idea.

Right-click the shortcut and say edit item (or shortcut, or whatever may be closest to that...I have Kubuntu which uses KDE not Gnome). Set the workpath to "/usr/local/bin" and apply that, then try it. If it doesn't work, search around for the folder where the program was installed (most likely to be in /usr or /usr/local directory). Once you find the executable "exe" for that program, put '/this/is/directory/of/command/exe' (example...and "exe" being the file itself) in the command section and leave the working path blank, then apply it. It should work after that.

I would just download the program but I have dial-up and I don't have time to get it. lol

---

### Post by Nubnut on 2008-05-21
The deb package downloaded directly to the desktop, then extracted to it's own folder on the desktop again, within this theres a usr/bin folder containing 2 files exe and run-exe.sh
Neither of these are opening the application!
eXe is one of those programs that opens within Firefox, btw, is this relevant?

---

### Post by zvacet on 2008-05-21
System>preferences>main menu>onthe left select education and then on the right new item.That will create launcher in which youi will type

1.name = name of program
2.command = browse to the usr/bin and select run-exe.sh
3.icon = look in usr/share/pixmaps (if that is important)

You are just create launcher for your program which works in Firefox.i hope this is helpful to you.Good luck with teaching.

---

