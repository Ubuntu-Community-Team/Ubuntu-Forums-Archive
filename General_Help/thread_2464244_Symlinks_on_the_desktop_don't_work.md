---
title: "Symlinks on the desktop don't work"
date: 2021-06-27
forum: General Help
---

### Post by golfdiesel on 2021-06-27
I have a weird issue after upgrading to 20.04.
With the previous version I made some symlinks to AppImages to the desktop but after the upgrade they didn't work anymore. 
I removed those symlinks and re-created them but when I double click them nothing happens. 
When I open a terminal window and go to the Desktop folder and run the symlink from there it works perfectly. So the symlink is correct but I can't start it by double clicking the symlink on the desktop.

Is there any solution to this?

---

### Post by scorp123 on 2021-06-27
> **golfdiesel said:**
>  So the symlink is correct but I can't start it by double clicking the symlink on the desktop.

What are the permissions on those and on the symlink targets?

---

### Post by golfdiesel on 2021-06-27
Symlink on desktop: 
lrwxrwxrwx 1 remco remco    69 jun 27 13:50 FreeCAD -> ../Appimages/FreeCAD_0.19-24291-Linux-Conda_glibc2.12-x86_64.AppImage

Target in my Appimages folder: 
-rwxrwxr-x 1 remco remco 847320256 mei  9 20:29 FreeCAD_0.19-24291-Linux-Conda_glibc2.12-x86_64.AppImage

---

### Post by scorp123 on 2021-06-27
> **golfdiesel said:**
>  but when I double click them nothing happens. 

Same issue maybe?
[https://askubuntu.com/questions/1266721/cant-run-appimage-on-desktop-by-doubleclicking-or-clicking-open]("https://askubuntu.com/questions/1266721/cant-run-appimage-on-desktop-by-doubleclicking-or-clicking-open")

---

### Post by golfdiesel on 2021-06-27
Yes that is the same issue!

This is the solution that worked for me.

[https://askubuntu.com/a/1337991]("https://askubuntu.com/a/1337991")

> I've had the same issue and yes, making the file executable is necessary, however, to be able to open the appimage from desktop you will have to:

Right click on your desktop
Click on Settings
Scroll down to the bottom and look for Action to do when launching a program from the desktop
Click the drop down menu on the right of it and set it to Launch the file
Now launching the appimage from the desktop by clicking on it should work. At least this did it for me.

---

### Post by monkeybrain20122 on 2021-06-27
It is a feature not a bug, gnome has removed the ability to launch binaries by right clicking from Nautilus
[https://www.linuxuprising.com/2018/05/nautilus-will-no-longer-launch-binaries.html](https://www.linuxuprising.com/2018/05/nautilus-will-no-longer-launch-binaries.html)

You can create a .desktop file for the appimage and place it in .local/share/applications and it will show up in the dash (though clicking it in .local/share/applications won't work like before) From there you can launch the appimage.

Nautilus is getting wierder and more frustrating to use with every new gnome release, I have switched to nemo as the default file manager (I use unity, but this works in gnome session as well)

---

### Post by vanadium on 2021-06-28
A .desktop file can also be put on the desktop to launch it from there.

Actually, it is not nautilus that is to blame here, because nautilus in 20.04 has been taken off the job of managing the desktop. Instead, a Gnome Shell extension is managing the desktop. It is quite premature and limited in functioning. In 21.04, it was replaced by a better fork, Desktop Extensions NG. You may consider disabling the default Desktop Icons extension and install the NG one from the Gnome Shell extensions website.

---

