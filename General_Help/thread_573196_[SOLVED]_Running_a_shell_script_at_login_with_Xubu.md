---
title: "[SOLVED] Running a shell script at login with Xubuntu"
date: 2007-10-11
forum: General Help
---

### Post by eriqjaffe on 2007-10-11
Howdy!

I'm running Xubuntu 7.04 as the basis for a digital picture frame, and I can't figure out how to get the shell script that kicks off the slideshow to run automatically when I log on.

The script itself is extremely simple:

```
#!/bin/sh

unclutter -idle 2 &
feh /home/eriq/Pictures/*.* -z -F -D 15
```

I've set it to be executable, and it works fine if I launch it manually, but I'm not sure where I need to put it and what I need to do to get it to autostart.  Any help would be appreciated.  Thanks!

---

### Post by Vixis on 2007-10-11
Try System -> Preferences -> Sessions
then New, in the Command add path to your script

---

### Post by por100pre1 on 2007-10-11
```
touch ~/.config/autostart/unclutter.desktop
```

```
mousepad ~/.config/autostart/unclutter.desktop
```

and add this to the file:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=unclutter
Exec=/home/*your-user-name*/*script-name*.sh
X-GNOME-Autostart-enabled=true

```
mousepad ~/.config/xfce4-session/xfce4-session.rc
```

Check that LaunchGnome is set to true.

---

### Post by eriqjaffe on 2007-10-11
> **por100pre1 said:**
> ```
touch ~/.config/autostart/unclutter.desktop
```

```
mousepad ~/.config/autostart/unclutter.desktop
```

and add this to the file:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=unclutter
Exec=/home/*your-user-name*/*script-name*.sh
X-GNOME-Autostart-enabled=true

```
mousepad ~/.config/xfce4-session/xfce4-session.rc
```

Check that LaunchGnome is set to true.Thanks, that got it working.

Granted, I'm not really sure what I just did exactly, but...  :)

---

### Post by por100pre1 on 2007-10-11
> **eriqjaffe said:**
> Thanks, that got it working.

Granted, I'm not really sure what I just did exactly, but...  :)

You just added your script to GNOME sessions which are also loaded by Xubuntu's XFCE. Typically, Ubuntu users add the script using gnome-session-properties but you just did it manually. Glad to help! :)

---

