---
title: "creating launcher in Ubuntu 12.04"
date: 2014-12-02
forum: General Help
---

### Post by vaina on 2014-12-02
Hi, I need a launcher and tried to create a *.desktop* file, but anything happens when I run it.```
[Desktop Entry]
Version=1.0
Name=CAESES-FFW
Comment=free and limited version of FRIENDSHIP-Framework
Exec=/opt/CAESES-FFW_3.1.2_Linux.x86_64/CAESES-FFW
Icon=/opt/CAESES-FFW_3.1.2_Linux.x86_64/CAESES-FFW.ico
Terminal=false
Type=Application
Categories=Science;
```
I save the *.desktop* file in **/opt/share/applications** and make it executable with```
sudo chmod +x CAESES-FFW.desktop
```
What's wrong with my settings, please?

---

### Post by CantankRus on 2014-12-02
You should place the .desktop file in **~/.local/share/applications** and it doesn't need to be executable unless you're placing a shortcut or copying to the desktop.

Does the application start in terminal with...
```
/opt/CAESES-FFW_3.1.2_Linux.x86_64/CAESES-FFW
```
or 
do you need to cd to the **/opt/CAESES-FFW_3.1.2_Linux.x86_64** directory first.

Try adding a **Path=** line to the .desktop ```
Path=/opt/CAESES-FFW_3.1.2_Linux.x86_64
```

---

### Post by vaina on 2014-12-02
Thanks for your reply, CantankRus. I've followed your tip and moved the *.desktop* file in **~/.local/share/applications** (I'm the only one user anyway).
I need to enter the software folder, before launching the script. I added a Path line to the file (I just renamed the folder name)```
[Desktop Entry]
Version=1.0
Name=CAESES-FFW
Comment=free and limited version of FRIENDSHIP-Framework
Path=/opt/CAESES-FFW
Exec=$Path/CAESES-FFW
Icon=$Path/CAESES-FFW.ico
Terminal=false
Type=Application
Categories=Science;
```
Is that what you meant? Anyway, it seems not to work :-(

---

### Post by CantankRus on 2014-12-02
Putting the .desktop in  ~/.local/share/applications will allow it to be listed in the applications menu.

Don't use **$Path**.
Use the full path.
 
This thread deals with a similar situation... [http://ubuntuforums.org/showthread.php?t=2253822](http://ubuntuforums.org/showthread.php?t=2253822)
Can't really test these things because I don't use either of these applications.

---

### Post by vaina on 2014-12-02
I read the thread you linked and I edited the *.desktop* file, but it still doesn't work.
In the meantime, I found out that in a software subfolder there is a script to create a desktop launcher```
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon=/opt/CAESES-FFW/media/img/ficon1.ico
Name=CAESES-FFW
Exec=/opt/CAESES-FFW/CAESES-FFW
Name=CAESES-FFW
```
on the desktop: I simply moved it in *~/.local/share/application* folder. I can't understand the reason, but this one works and I can lock it in the launcher without problems.

---

