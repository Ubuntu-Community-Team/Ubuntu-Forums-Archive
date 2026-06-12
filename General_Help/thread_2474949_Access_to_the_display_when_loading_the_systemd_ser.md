---
title: "Access to the display when loading the systemd service"
date: 2022-05-12
forum: General Help
---

### Post by akexanderzhirov on 2022-05-12
I am writing a bootable service in C and D languages.

There is a database of users with thin client settings. I access this database over the network during the download and get from there the data of a specific user linked to the MAC address. The fact is that a user can have two or more monitors connected to a thin client. Data for each monitor is also loaded from the database. Using the xrandr source code, I wrote a program that, knowing the monitor ID, sets the desired monitor in one position or another. The fact is that xrandr uses the global variable DISPLAY, which is unavailable during the loading process.

[HTML]&#9679; myservice-init.service - myservice
     Loaded: loaded (/etc/systemd/system/myservice-init.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Thu 2022-05-12 19:15:14 MSK; 55s ago
    Process: 1559 ExecStart=/etc/init.d/myservice-init (code=exited, status=1/FAILURE)
   Main PID: 1559 (code=exited, status=1/FAILURE)

&#1084;&#1072;&#1103; 12 19:15:14 ts_d85ed3156a39 systemd[1]: Starting myservice...
&#1084;&#1072;&#1103; 12 19:15:14 ts_d85ed3156a39 thinstation[1562]: Can't open display :0
&#1084;&#1072;&#1103; 12 19:15:14 ts_d85ed3156a39 systemd[1]: myservice-init.service: Main process exited, code=exited, status=1/FAILURE
&#1084;&#1072;&#1103; 12 19:15:14 ts_d85ed3156a39 systemd[1]: myservice-init.service: Failed with result 'exit-code'.
&#1084;&#1072;&#1103; 12 19:15:14 ts_d85ed3156a39 systemd[1]: Failed to start myservice.[/HTML]


Although, looking at the Xorg service - this data is there:

```
~# cat /etc/X11/xinit/xinitrc.d/50-systemd-user.sh 

#!/bin/sh

systemctl --user import-environment DISPLAY XAUTHORITY

if command -v dbus-update-activation-environment >/dev/null 2>&1; then
    dbus-update-activation-environment DISPLAY XAUTHORITY
fi
```

And I start my service after downloading xorg.service. But even adding this code to the launch of my service, I still get errors:

```
&#9679; myservice-init.service - myservice
     Loaded: loaded (/etc/systemd/system/myservice-init.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Thu 2022-05-12 19:08:52 MSK; 18s ago
    Process: 1560 ExecStart=/etc/init.d/myservice-init (code=exited, status=1/FAILURE)
   Main PID: 1560 (code=exited, status=1/FAILURE)

May 12 19:08:52 ts_d85ed3156a39 systemd[1]: Starting myservice...
May 12 19:08:52 ts_d85ed3156a39 thinstation[1564]: dbus-update-activation-environment: error: unable to connect to D-Bus: Unable to autolaun
May 12 19:08:52 ts_d85ed3156a39 thinstation[1570]: Can't open display :0
May 12 19:08:52 ts_d85ed3156a39 systemd[1]: myservice-init.service: Main process exited, code=exited, status=1/FAILURE
May 12 19:08:52 ts_d85ed3156a39 systemd[1]: myservice-init.service: Failed with result 'exit-code'.
May 12 19:08:52 ts_d85ed3156a39 systemd[1]: Failed to start myservice.

```

And if I just launch my application, then it works out quite correctly:

```

IFace("enp3s0", "e8:5b:d2:11:6a:39", "192.168.0.15")
[Monitor("VGA-1", true, 1280, 1024)]

```

---

