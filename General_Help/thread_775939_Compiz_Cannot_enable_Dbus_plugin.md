---
title: "Compiz: Cannot enable Dbus plugin"
date: 2008-04-30
forum: General Help
---

### Post by GhodMode on 2008-04-30
I can't enable the Dbus plugin in the CompizConfig Settings Manager (ccsm).  When I try, the check appears in the box for a moment, then disappears.

**[color=navy]Can anyone help me to correct this problem?[/color]**

If I monitor the [FONT=Courier New].xsession-errors[/FONT] file for related messages, I see that compiz is trying to launch dbus, even though it's already running.  **[color=navy]Is it supposed to launch dbus, or try to connect to the existing session?[/color]**

```
$ tail -f /home/ghodmode/.xsession-errors | grep compiz
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (mag) - Warn: Could not load magnifier overlay image "Gnome/overlay.png"!
/usr/bin/compiz.real (mag) - Warn: Could not load magnifier overlay image "Oxygen/overlay.png"!
/usr/bin/compiz.real (mag) - Warn: Could not load magnifier overlay image "Oxygen/overlay.png"!
```

([color=navy]The magnifier overlay is an unrelated problem, isn't it?[/color])

```
$ ps -ef | grep dbus | grep -v grep
1000      7458     1  0 Apr30 ?        00:00:00 dbus-launch --autolaunch a93d466e491f266455ca1e2d48172af0 --binary-syntax --close-stderr
1000      7459     1  0 Apr30 ?        00:00:00 /usr/bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
106       9230     1  0 02:12 ?        00:00:00 /usr/bin/dbus-daemon --system
```

More information:
**_Kubuntu 8.04 (Hardy Heron)_**
**_Video Adapter / Driver_**```
$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

$ dmesg | grep -i nvidia
[   56.714594] nvidia: module license 'NVIDIA' taints kernel.
[   59.255946] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
```

**_KDE_**```
KDE
kdesktop --version
Qt: 3.3.8b
KDE: 3.5.9
KDesktop: 3.5.9
```

**_Compiz-Fusion_**```
Compiz:
#dpkg-query -l | grep compiz | awk '{printf( "%-30s\t%s\n", $2, $3);}'
compiz                          1:0.7.4-0ubuntu6
compiz-core                     1:0.7.4-0ubuntu6
compiz-fusion-plugins-extra     0.7.4-0ubuntu1
compiz-fusion-plugins-main      0.7.4-0ubuntu4
compiz-gnome                    1:0.7.4-0ubuntu6
compiz-kde                      1:0.7.4-0ubuntu6
compiz-plugins                  1:0.7.4-0ubuntu6
compizconfig-backend-gconf      0.7.4-0ubuntu1
compizconfig-backend-kconfig    0.7.4-0ubuntu1
compizconfig-settings-manager   0.7.4-0ubuntu2
desktop-effects-kde             0.4
emerald                         0.7.2-0ubuntu2
kicker-compiz                   3.5.4-0ubuntu1
kicker-taskbar-compiz           0.1-0ubuntu1
libcompizconfig0                0.7.4-0ubuntu1
libemeraldengine0               0.7.2-0ubuntu2
python-compizconfig             0.7.4-0ubuntu1
```

Thank you.

--
-- Ghodmode

---

### Post by JohnnyWhite2007 on 2008-06-04
I am having the same problem with all the new plugins, it's really annoying.

---

### Post by ChompTheMan on 2008-06-05
I am having the same issue.

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
```

```
$ kdesktop --version
Qt: 3.3.8b
KDE: 3.5.9
KDesktop: 3.5.9
```

```
$ dpkg-query -l | grep compiz | awk '{printf( "%-30s\t%s\n", $2, $3);}'
compiz-bcop                     0.7.4-0ubuntu1
compiz-core                     1:0.7.4-0ubuntu6
compiz-dev                      1:0.7.4-0ubuntu6
compiz-fusion-plugins-extra     0.7.4-0ubuntu1
compiz-fusion-plugins-main      0.7.4-0ubuntu5
compiz-gnome                    1:0.7.4-0ubuntu6
compiz-kde                      1:0.7.4-0ubuntu6
compiz-plugins                  1:0.7.4-0ubuntu6
compizconfig-backend-kconfig    0.7.4-0ubuntu1
compizconfig-settings-manager   0.7.4-0ubuntu2
emerald                         0.7.2-0ubuntu2
kicker-compiz                   3.5.4-0ubuntu1
kicker-taskbar-compiz           0.1-0ubuntu1
libcompizconfig0                0.7.4-0ubuntu1
libemeraldengine0               0.7.2-0ubuntu2
python-compizconfig             0.7.4-0ubuntu1
```

---

### Post by twothird on 2008-06-09
same here. what happened was, it didn't work at first, so I installed some more dbus packages, the most important of which seemed to be kdbus

but it still didn't work. so i enabled glib first, and then tried to enable dbus. it worked then.

i needed dbus for a plugin for Kadu, that notifies me with the compiz water effect whenever i get a new message. so, basically, it was working all good, until i activated the option TITLE WAVE in compiz water effect preferences. It was still working, till i tried to do something that caused the water effect there to activate (which made waves come out from the window title). i then got a message that dbus crashed, and emerald crashed at the same time. Kadu was working at that moment, too - so there possibly was a conflict.

anyway, i couldn't get dbus to work again after that. thought of removing the dbus package, but it wants to remove my awn and compiz packages at the same time, something that i don't really want to do. 

any ideas?

---

### Post by tasos on 2008-07-05
Is the dbus daemon running?

[http://wiki.compiz-fusion.org/Plugins/Dbus](http://wiki.compiz-fusion.org/Plugins/Dbus)

---

### Post by TB2 on 2008-09-20
I have the exact same problem. Any solutions yet?

---

### Post by TB2 on 2008-09-20
And now, here's the freakin' simple solution. After 3 hours of digging and swearing, this simple thing solved the problem:

Found [here](http://gentoo-wiki.com/TIP_D-BUS_Session_Bus_with_KDM)

> To enable a D-BUS session bus for a single account, we will take advantage of an optional feature I discovered while digging through the startkde script. 

Simply create the following file and give yourself read and execute permissions. (the ~/.kde/env directory probably won't exist. Just create it.)

```
File: ~/.kde/env/start_dbus_session_bus.sh 
 
# test for an existing bus daemon, just to be safe
if test -z "$DBUS_SESSION_BUS_ADDRESS" ; then
        # if not found, launch a new one
        eval `dbus-launch --sh-syntax --exit-with-session`
fi
```

All you need to do now is log out. The session bus will now start every time you log in, and exit when you log out.

---

