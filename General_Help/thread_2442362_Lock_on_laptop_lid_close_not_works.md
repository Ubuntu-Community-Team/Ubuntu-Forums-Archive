---
title: "Lock on laptop lid close not works"
date: 2020-05-02
forum: General Help
---

### Post by whynvidia on 2020-05-02
Hello,

Using Ubuntu 20.04 LTS GNOME, $XDG_SESSION_TYPE shows X11

I downloaded gnome-tweaks and disabled: Suspend when laptop lid is closed

then edit: ```
/etc/systemd/logind.conf
```and after ```
[Login] 
```add the line: ```
HandleLidSwitch=lock

```then I restarted. 

Then, I closed the laptop lid but it doesn't lock the screen!

This all from [https://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid](https://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid) before above, I ran > [COLOR=#242729][FONT=Consolas]sudo service systemd-logind restart
[/FONT][/COLOR]
[COLOR=#242729][FONT=Consolas]but it doesn't do anything just show Lenovo Screen so I go to tty1 and restarted.[/FONT][/COLOR]


file etc/systemd/logind.conf:
```
[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
#InhibitDelayMaxSec=5
HandlePowerKey=ignore
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
HandleLidSwitch=lock
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#HoldoffTimeoutSec=30s
#IdleAction=ignore
#IdleActionSec=30min
#RuntimeDirectorySize=10%
#RemoveIPC=yes
#InhibitorsMax=8192
#SessionsMax=8192

```
I installed gnome-tweaks and removed  [COLOR=#2E2E2E][FONT=-apple-system]ignore-lid-switch-tweak from startup[/FONT][/COLOR]

Couldn't make this work! Back when I used Debian, ALL I HAD TO DO WAS TO SELECT IT IN THE SETTINGS

UPDATE #2

A report from today, I did modifications which cause it to work but then I tried to close lid and not works.

gnome-tweaks:

* Suspend when laptop lid is closed is enabled

File /etc/systemd/logind.conf

```

  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See logind.conf(5) for details.


[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
#InhibitDelayMaxSec=5
HandlePowerKey=ignore
HandleSuspendKey=ignore
HandleHibernateKey=ignore
HandleLidSwitch=suspend
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#HoldoffTimeoutSec=30s
#IdleAction=ignore
#IdleActionSec=30min
#RuntimeDirectorySize=10%
#RemoveIPC=yes
#InhibitorsMax=8192
#SessionsMax=8192

```


After closing lid and open screen doesn't lock nor suspends and shows that lid is closed
```

$ sudo systemctl status systemd-logind

May 03 17:54:51 home systemd-logind[1044]: Lid closed.



```


Info if something override the suspend/locking screen?
```

systemd-inhibit | grep block
gdm                          125  gdm  1566 gsd-media-keys  handle-power-key:handle-suspend-key:handle-hibernate-key GNOME handling keypresses                                 block
user                         1000 hiro 2125 gsd-media-keys  handle-power-key:handle-suspend-key:handle-hibernate-key GNOME handling keypresses                                 block

```

I suspect that ```
HandleLidSwitch
``` modified while I was working but how is that I didn't restart causing ```
systemd-logind
``` to modified?


UPDATE3:

I reset all settings using gnome-tweaks, comment all ```
/etc/systemd/user.conf
``` then I restarted the laptop. After the restart I closed the lid but laptop not is suspending!
Someone suggest to [COLOR=#22231F][FONT=&amp]see if the system is able to suspend at all, by running "systemctl suspend" in a terminal so I got an error because I played a music[/FONT][/COLOR]```
Operation inhibited by "user" (PID 2123 "gnome-session-b", user user), reason is "user session inhibited".Please retry operation after closing inhibitors and logging out other users.
Alternatively, ignore inhibitors and users with 'systemctl suspend -i'.

```
[COLOR=#22231F][FONT=&amp]but when I try to close the lid it doesn't suspend.[/FONT][/COLOR]

---

### Post by whynvidia on 2020-05-02
see edit

---

### Post by whynvidia on 2020-05-03
edit2

---

