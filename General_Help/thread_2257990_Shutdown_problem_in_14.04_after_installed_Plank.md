---
title: "Shutdown problem in 14.04 after installed Plank"
date: 2014-12-23
forum: General Help
---

### Post by czgirb on 2014-12-23
currently i'm using **ubuntu 14.04 classic fallback**
below is some questions regarding to **plank dock**

**1**
Previously, all my button works normally, After installed Plank Dock, the Top Panel's OFF sign still show all available Options, but **Log-Out**, **Restart**, and **Shutdown** won't works.
in order to turn OFF the computer, it required me to run **shutdown** command directly from **terminal**
*** the shutdown will **back to normal if i quit plank**

2
how to make plank automatically run at startup without interrupting other programs? i've tried :
* **name: plank --- command: plank --- commend: none**
* **name: plank --- command: sh -c "sleep 5 && usr/bin/plank" --- commend: none**
but no one works
please guide me

**Thank you in advance**

---

### Post by kerry_s on 2014-12-24
plank shouldn't have no effect on the top panel. it's a totally different program.

just add it to your start up:
name: plank
command: plank

i'm using docky, but it's the exact same thing just different name & icon.

---

### Post by CantankRus on 2014-12-24
> **kerry_s said:**
> plank shouldn't have no effect on the top panel. it's a totally different program.

just add it to your start up:
name: plank
command: plank

i'm using docky, but it's the exact same thing just different name & icon.

It shouldn't but I am seeing exactly the same as czgirb in the flashback metacity session.
I didn't realize plank was causing this until I read czgirb's post. Just thought it was a panel bug.

Kill plank and the logout menu starts to work.
This is using the **indicator applet complete** menu which is default.
If I add the **User Menu** applet I can use that logout whether plank is running or not.

[COLOR="#FF0000"]EDIT[/COLOR]:
Found bug report... [https://bugs.launchpad.net/plank/+bug/1245490](https://bugs.launchpad.net/plank/+bug/1245490)
See post #4 for eplanation.

---

### Post by kerry_s on 2014-12-24
i guess for now, it would be best just to quit plank when you need to use those options. it's just a simple right click-> quit on the icon.

---

### Post by CantankRus on 2014-12-24
You could make your own logout/shutdown button for plank.

```
gedit ~/.local/share/applications/Exit.desktop
```
Copy and paste in...
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=gnome-session-quit
Name=Exit
Icon=system-log-out
Name[en_AU]=Exit

Actions=Shutdown;

[Desktop Action Shutdown]
Name=Shutdown
Exec=gnome-session-quit --power-off
```
Save and close.

In the file browser go to **~/.local/share/applications** and drag and drop **Exit.desktop** onto Plank.

---

### Post by kerry_s on 2014-12-24
> **CantankRus said:**
> You could make your own logout/shutdown button for plank.

```
gedit ~/.local/share/applications/Exit.desktop
```
Copy and paste in...
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=gnome-session-quit
Name=Exit
Icon=system-log-out
Name[en_AU]=Exit

Actions=Shutdown;

[Desktop Action Shutdown]
Name=Shutdown
Exec=gnome-session-quit --power-off
```
Save and close.

In the file browser go to **~/.local/share/applications** and drag and drop **Exit.desktop** onto Plank.


or just install power-commands & just drag them to plank. i have them on the desktop, see pic above.

[http://linuxg.net/how-to-install-power-commands-1-6-on-ubuntu-14-04-trusty-tahr-via-ppa/](http://linuxg.net/how-to-install-power-commands-1-6-on-ubuntu-14-04-trusty-tahr-via-ppa/)

---

### Post by mcvries on 2014-12-24
Not using plank anymore, but i had the same problem. I found that if i started Plank with a delay the problem would occur less frequently.

And the problem is in the dialogue to be displayed, so if you use this:

[COLOR=#000000][FONT=Tahoma]    You can suppress confirmation dialogues by running this command[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]    Code:[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]    gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true

You will have the option to shutdown directly from the panel and plank won't be a problem anymore
[/FONT][/COLOR]

---

### Post by czgirb on 2014-12-24
Thank you for all answer given ... will try tonight

Is there somebody who are willing to guide me for telling me how to add **Recycle Bin** in **Plank**?
Cos when I drag **Recycle Bin** icon from **Nautilus**, it become **File Manager** in **Plank** ... so I unable to inform whether it was in **FULL** or **EMPTY**.

---

### Post by kerry_s on 2014-12-24
i don't think you can get a working trash can on plank

---

### Post by zackskrip on 2015-01-21
Sorry for necroposting, but I tried to delay plank by typing in "sleep 20;" at the beginning of the command field when editing under "Startup Applications" but then it wouldn't start at all. How do I get it to delay? Thanks for your help.

---

### Post by CantankRus on 2015-01-21
In the command field use
```
sh -c "sleep 20 && plank"
```

---

### Post by kerry_s on 2015-01-21
put it in a script & call the script.

#!/bin/sh
sleep 20
plank &
exit 0

---

### Post by zackskrip on 2015-01-21
That worked great. Thanks so much for your help!

---

