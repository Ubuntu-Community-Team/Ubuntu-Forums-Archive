---
title: "script as start up app"
date: 2014-05-03
forum: General Help
---

### Post by kurja on 2014-05-03
I made a script, tested that it works fine and added it to startup applications in stock gui, but apparently it doesn't run at start up. What logs might I look at to troubleshoot this? In what file did the gui add my execute script command?

---

### Post by warp99 on 2014-05-03
There could be numerous factors why the script is not running. Can you post the script?

---

### Post by deadflowr on 2014-05-03
> **kurja said:**
> In what file did the gui add my execute script command?

```
~/.config/autostart
```

This is where the startup application files are.(Locally, meaning non-system-wide, user startups)
It should be a .desktop file. Usually whatever-you-named-it.desktop.

If it doesn't open on a simple click, you can open gedit and then open it from there to read it.

---

### Post by kurja on 2014-05-03
Script that I made is is ~/bin/xsetwacom.sh ```
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 1 "key ctrl z"
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 9 "key shift"
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 8 "key ctrl"
xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 3 "key alt"

```
at ~/.config/autostart/ I found .xsetwacom.sh.desktop, containing ```
[Desktop Entry]
Type=Application
Exec=/home/k/bin/xsetwacom.sh
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en]=xsetwacom
Name=xsetwacom
Comment[en]=undonappi
Comment=undonappi

```

edit, the script does what it's supposed to when I run it manually, but I have to do it after every boot to get wacom buttons configured.

---

### Post by warp99 on 2014-05-03
Just put the commands in your ~/.bashrc script.

---

### Post by kurja on 2014-05-03
I gather that would work for sure, but I'd like to know why this setup doesn't work, if there's any explanation..?

---

### Post by steeldriver on 2014-05-03
It's likely an issue of the shell environment not having everything it needs to execute the commands - possibly just a matter of not having the path for the xsetwacom executable, although it would be good to specify a shell interpreter (/bin/bash or /bin/sh) explicitly as well

```

#!/bin/bash

/usr/bin/xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 1 "key ctrl z"
/usr/bin/xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 9 "key shift"
/usr/bin/xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 8 "key ctrl"
/usr/bin/xsetwacom set "Wacom Bamboo 16FG 4x5 Finger pad" Button 3 "key alt"

```

---

