---
title: "larger mouse"
date: 2015-03-11
forum: General Help
---

### Post by jazzbo2 on 2015-03-11
how do I install larger mouse in Ubuntu ?

 Saw this but how do you install ?

[FONT=arial]larger mouse cursors for X[/FONT]

[FONT=arial]https://apps.ubuntu.com/cat/applications/big-cursor/[/FONT]

---

### Post by Holger_Gehrke on 2015-03-11
That's basically a font full of mouse-cursor symbols for people who are using X and a window manager without a Desktop Environment. So if you're using one of the major DEs (Unity, Gnome, KDE, XFCE or LXDE) this is completely useless to you. How to change the mouse cursor size depends on your DE, some offer a GUI for it, in others you have to edit a configuration file.

---

### Post by jazzbo2 on 2015-03-11
I just want a bigger pointer, can you advise how to install ?

---

### Post by Holger_Gehrke on 2015-03-11
If you're using Unity (the standard Ubuntu desktop) there's a thread discussing this problem and a solution [here]("http://ubuntuforums.org/showthread.php?t=2048046&page=4&p=12994288#post12994288").

---

### Post by CantankRus on 2015-03-11
This works in Ubuntu Trusty 14.04.
You can increase the size of the default cursor (DMZ-White) by running these commands.

[SIZE=3]**1)**[/SIZE] Firstly set the cursor back to default if you have changed....(run each line separately)...
```
gsettings reset org.gnome.desktop.interface cursor-theme
sudo update-alternatives --set x-cursor-theme /usr/share/icons/DMZ-White/cursor.theme
```

[SIZE=3]**2)**[/SIZE] To increase size...
```
gsettings set com.canonical.Unity.Interface cursor-scale-factor **1.35**
echo "Xcursor.size:**32**" > ~/.Xresources
```
Log out and back in.

For an even larger cursor run....
```
gsettings set com.canonical.Unity.Interface cursor-scale-factor **2**
echo "Xcursor.size:**48**" > ~/.Xresources
```
Log out and back in.

---

