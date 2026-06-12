---
title: "Error when try to launch photoshop 7"
date: 2006-12-13
forum: General Help
---

### Post by Magiczero on 2006-12-13
hi

When I launch photoshop from my desktop i get this error:

> Details: Failed to execute child process "/home/tanner/.wine/drive_c/Program" (No such file or directory)

Does anybody know what this means?

Thanks

---

### Post by bodhi.zazen on 2006-12-13
> **Magiczero said:**
> hi

When I launch photoshop from my desktop i get this error:



Does anybody know what this means?

Thanks

Yes, you need to update the path. Linux does not like the space in "Program Files"

Open your menu editor and in the command line for your launcher change "Program Files" to "Program\ Files" and re-try.

---

### Post by Magiczero on 2006-12-18
hi

I hope someone can help me here. I have installed Adobe Photoshop 7.0 on my system and when I  click my icon I made on my desktop I get this error:  > There was an error launching the application. > Details: Failed to execute child process "/home/tanner/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/photoshop.exe" (No such file or directory) I have even made sure I have all the slashes in the command box of the launcher box but when I click the app shortcut it does not show the slashes in the right spot.  Can anyone tell me how to fix this issue?

Thanks

---

### Post by scxtt on 2006-12-18
try replacing

"/home/tanner/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/photoshop.exe"

with

"/home/tanner/.wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0/photoshop.exe"

---

### Post by Magiczero on 2006-12-18
hi

I hope someone can help me here. I have installed Adobe Photoshop 7.0 on my system and when I  click my icon I made on my desktop I get this error:  > There was an error launching the application. > Details: Failed to execute child process "/home/tanner/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/photoshop.exe" (No such file or directory) I have even made sure I have all the slashes in the command box of the launcher box but when I click the app shortcut it does not show the slashes in the right spot.  Can anyone tell me how to fix this issue?

I just tried a command and got this error: > tanner@tanner-desktop:~$ gksudo /home/tanner/.wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0/photoshop.exe

(gksudo:12528): Gtk-WARNING **: Unable to locate theme engine in module_path: "bluecurve",
GNOME_SUDO_PASS
sudo: 1 incorrect password attempt
sn_launcher_context_initiate called twice for the same SnLaunchContext
tanner@tanner-desktop:~$ 



Thanks

---

### Post by bodhi.zazen on 2006-12-18
Try without gksudo, just ```
wine /home/tanner/.wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0/photoshop.exe
```

---

