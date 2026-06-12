---
title: "Add shortcut to Ubuntu Launcher"
date: 2013-04-24
forum: General Help
---

### Post by SkylineGTR on 2013-04-24
Hi.

I am trying to add a shortcut to PyCharm IDE to Ubuntu Launcher (Ubuntu 13.04), but so far nothing is working.

I've created a file named "pycharm.desktop" in "/usr/shares/applications/" with this:

```
[Desktop Entry]
Version=1.0
Name=PyCharm

Exec=/home/username/pycharm-2.7.2/bin/pycharm.sh
Terminal=false
Icon==/home/username/pycharm-2.7.2/bin/pycharm.png
Type=Application
Categories=TextEditor;IDE;Development
X-Ayatana-Desktop-Shortcuts=NewWindow

[NewWindow Shortcut Group]
Name=New Window
Exec=/home/username/pycharm-2.7.2/bin/pycharm.sh
TargetEnvironment=Unity
```


I'm not seeing a PyCharm entry in Ubuntu Launcher with this... What may be wrong?
I used this process to add a shortcut for Sublime Text 2 and it works :\

Thanks :)

---

### Post by SkylineGTR on 2013-04-27
Anyone?

---

### Post by Thee on 2013-04-27
Try to put only this and see if it works:

```

[Desktop Entry]
Version=1.0
Name=PyCharm
Exec=/home/username/pycharm-2.7.2/bin/pycharm.sh
Terminal=false
Icon==/home/username/pycharm-2.7.2/bin/pycharm.png
Type=Application

```

---

### Post by SkylineGTR on 2013-04-28
It didn't work :(

---

### Post by howefield on 2013-04-28
Take it that you have been through the info here..

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

### Post by SkylineGTR on 2013-04-28
Thanks for the tutorial howefield.
Thee's script worked. I just needed to drag the shortcut from dash to the launcher after creating the .desktop file.

Thank you all.

---

### Post by kia-hosseini7 on 2014-02-16
Thanks for your code.

I think == should be = 
:)

---

