---
title: "Hplip problem on boot"
date: 2013-10-25
forum: General Help
---

### Post by hnasiet on 2013-10-25
[COLOR=#333333][FONT=Ubuntu Mono]On every new bootup, I get:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]"Sorry, Ubuntu 12.04 has experienced an internal error.......Excutable path /usr/share/hplip/systray.py"[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]then:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]"Could not determine the package or source package name"

It's very annoying[/FONT][/COLOR]

---

### Post by oldfred on 2013-10-25
Are you just getting the systray pop-up with the error?
I was getting it, but I run gnome-panel or fallback and assumed that was the issue. But I just close pop-up and never had an issue afterwards.

You should install the very newest hplip from HP and may need to change a setting.

HP Deskjet 3520
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup
# new version
hp-upgrade

No system tray error:
open up the "startup applications" editor from the admin menu.
add a new program, for the command put:
sleep 10;/usr/bin/hp-systray

---

### Post by hnasiet on 2013-11-03
sorry for the late reply, I installed the latest version but the problem persists.

---

### Post by oldfred on 2013-11-03
Did you try the setting?

---

### Post by hnasiet on 2013-11-09
yes, I've tried it. I'm just getting the pop-up, no issues afterwards. It doesn't seem to happen every time I boot-up. Yesterday, it happened, but today it didn't.

---

