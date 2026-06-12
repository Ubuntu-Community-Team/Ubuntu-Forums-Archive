---
title: "Unity Launcher Icons Question Mark"
date: 2015-03-25
forum: General Help
---

### Post by ozark_hillbilly on 2015-03-25
Certain applications (ie Text Editor, System Settings) when invoked and placed in the Launcher Bar leave a "?" for the icon. This is annoying as you must highlight the icon to see what  application the "?" icon actually represents?
Why were identifiable icons not assigned to these tasks? Is there an easy way to remedy this?

---

### Post by ozark_hillbilly on 2015-03-26
hmmmm....

---

### Post by CantankRus on 2015-03-26
Are you using the default icons.....**ubuntu-mono-dark**
Is gedit your text editor?
Check icon theme via terminal...
```
gsettings get org.gnome.desktop.interface icon-theme
```

Reset to default...
```
gsettings reset org.gnome.desktop.interface icon-theme
```

---

### Post by lads on 2015-11-11
I have had this issue since I upgraded to 14.04. Initially I thought this was related to wrong icon paths in the *.desktop* file, but this isn't the case:

```
$ cat /usr/share/applications/eclipse.mars.desktop
[Desktop Entry]
Type=Application
Name=Eclipse Mars
Icon=/usr/local/eclipse.mars/icon.xpm
Exec=env UBUNTU_MENUPROXY= /usr/local/eclipse.mars/eclipse
Terminal=false
Categories=Development;IDE;Java;

$ ls -la /usr/local/eclipse.mars/icon.xpm
-rwxr-xr-x 1 lads lads 140566 Sep  4 07:56 /usr/local/eclipse.mars/icon.xpm
```

For some time there was a work around that re-stored the icons:
1. Remove the icon from the launcher with right click and selecting *Unlock from Launcher*;
2. Open */usr/share/applications* with Nemo;
3. Drag and drop the corresponding item to the Launcher.

This only restored the icon temporarily and recently this work around stopped functioning with some applications (e.g. Eclipse). 

Moreover, this issue is affecting an increasing number of applications, right now about half of my Launcher items are shown with the famous grey question mark. Any hints on how to solve this are welcome.

Thank you.

---

