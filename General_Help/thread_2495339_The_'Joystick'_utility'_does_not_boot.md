---
title: "The 'Joystick' utility' does not boot"
date: 2024-02-15
forum: General Help
---

### Post by rooman62 on 2024-02-15
The 'Joystick' utility' does not boot correctly when I click on the application icon, it appears very briefly in the task bar then disappears.
I have remouved it and reinstalled it several times but all to no avail.
What can I do?


Ub 23.10 with latest updates.

---

### Post by Holger_Gehrke on 2024-02-15
Try to find the actual name of the program and call it from the command line. The program will most likely output additional diagnostics in the terminal window. To find the program search the *.desktop files in /usr/share/applications/ for the name shown in the application overview / menu.

Holger

---

### Post by rooman62 on 2024-02-20
tks, good idea, I'll do that.

---

### Post by rooman62 on 2024-02-20
The .desktop icon in /usr/share/applications/  is called jstest-gtk.desktop
I've tried;
jstest-gtk.desktop + ENTER
jstest-gtk + ENTER
./jstest-gtk + ENTER
/usr/share/applications/jstest-gtk.desktop + ENTER

I'vr tried L clicks, R clicks, double clicks etc, etc from /Home/ and in the folder with and without sudo.

all I get is file unknown or command not found. I have again uninstalled "Joystick" and re-installed it many times!

---

### Post by deadflowr on 2024-02-20
Find the Exec line in the desktop file
look at 
```
grep Exec= /usr/share/applications/jstest-gtk.desktop
```
the exec is the command that runs the app.
Exclude the Exec= part of the line and just run the command that comes after it.

---

### Post by rooman62 on 2024-02-20
I found jstest-gtk
when I try to launch it I get > impossible to open data/generic.png no file or folder of this type

---

### Post by rooman62 on 2024-02-20
Found an answer here
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1051546](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=1051546)

thanks for your help

---

