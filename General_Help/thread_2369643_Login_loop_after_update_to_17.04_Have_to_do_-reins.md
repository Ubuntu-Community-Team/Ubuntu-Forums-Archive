---
title: "Login loop after update to 17.04 Have to do -reinstall ubuntu-desktop and dpkg-reconf"
date: 2017-08-25
forum: General Help
---

### Post by pkdev on 2017-08-25
[COLOR=#111111][FONT=Ubuntu]After update to 17.04 from 16.10 i have problem with login loop.I was searching forums but nothing helps.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've tried ```
sudo chown username:username .Xauthority
```, ```
sudo chmod a+wt /tmp
``` with no luck, also reinstalled nvidia drivers. Nothing helps
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Checked ```
/var/log/Xorg.0.log
``` and ```
~/.xserver-errors
``` - no errors
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have to do ```
sudo dpkg-reconfigure lightdm sudo apt-get install --reinstall ubuntu-desktop
``` every time system boot up and then when i do sudo reboot Im able to login without loop error.

 How to fix this permanently?
Please help[/FONT][/COLOR]

---

