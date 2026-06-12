---
title: "Ubunt19.10 - VNC error: control process exited with error code; Couldn't add screen"
date: 2019-11-17
forum: General Help
---

### Post by makem2 on 2019-11-17
The Ubuntu 19.10 server system is running on a Pi4, headless.

I have a working instance of tightvnc server running but have to start it manually with the command 'vncserver' Attempts to get it to auto start on boot have failed.

I used the guide below to install the vnc server, the only difference being in the xstartup file which I could not get running using the entry in that guide.

[URL="https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04"]https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-18-04
[/URL]

```

makem@ubuntu:~$ vncserver

New 'X' desktop is ubuntu:1

Starting applications specified in /home/makem/.vnc/xstartup
Log file is /home/makem/.vnc/ubuntu:1.log
makem@ubuntu:~$

```

I added the following code:

```

sudo nano /etc/systemd/system/vncserver@.service
[Unit]
Description=Start TightVNC server at startup
After=syslog.target network.target

[Service]
Type=forking
User=makem
Group=makem
WorkingDirectory=/home/makem

PIDFile=/home/makem/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 :%i
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target
```

```

sudo systemctl daemon-reload
sudo systemctl enable vncserver@1.service
vncserver -kill :1
sudo systemctl start vncserver@1
Job for vncserver@1.service failed because the control process exited with error code.
See "systemctl status vncserver@1.service" and "journalctl -xe" for details.

```

```

makem@ubuntu:~$ journalctl -xe
Hint: You are currently not seeing messages from other users and the system.
      Users in groups 'adm', 'systemd-journal' can see all messages.
      Pass -q to turn off this notice.
-- 
-- The process' exit code is 'exited' and its exit status is 1.
Nov 17 20:37:38 ubuntu systemd[1674]: xfce4-notifyd.service: Failed with result 'exit-code
-- Subject: Unit failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- The unit UNIT has entered the 'failed' state with result 'exit-code'.
Nov 17 20:37:38 ubuntu systemd[1674]: Failed to start XFCE notifications service.
-- Subject: A start job for unit UNIT has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- A start job for unit UNIT has finished with a failure.
-- 
-- The job identifier is 194 and the job result is failed.
Nov 17 20:38:03 ubuntu dbus-daemon[1709]: [session uid=1001 pid=1709] Activating service n
Nov 17 20:38:03 ubuntu gnome-screensav[2620]: Locale not supported by C library.
                                                      Using the fallback 'C' locale.
Nov 17 20:38:03 ubuntu org.gnome.ScreenSaver[1709]: Unable to init server: Could not conne
Nov 17 20:38:03 ubuntu gnome-screensav[2620]: Cannot open display: 
Nov 17 20:38:03 ubuntu dbus-daemon[1709]: [session uid=1001 pid=1709] Activated service 'o
Nov 17 20:39:38 ubuntu dbus-daemon[1709]: [session uid=1001 pid=1709] Failed to activate s
makem@ubuntu:~$ 

```

```

makem@ubuntu:~$ systemctl status vncserver@1.service
&#9679; vncserver@1.service - Start TightVNC server at startup
   Loaded: loaded (/etc/systemd/system/vncserver@.service; enabled; vendor preset: enabled
   Active: failed (Result: exit-code) since Sun 2019-11-17 20:33:51 UTC; 8min ago
  Process: 2435 ExecStartPre=/usr/bin/vncserver -kill :1 > /dev/null 2>&1 (code=exited, st
  Process: 2439 ExecStart=/usr/bin/vncserver -depth 32 -geometry 1920x1080 :1 (code=exited

Nov 17 20:33:51 ubuntu vncserver[2439]: 17/11/19 20:33:50 Xvnc version TightVNC-1.3.10
Nov 17 20:33:51 ubuntu vncserver[2439]: 17/11/19 20:33:50 Copyright (C) 2000-2009 TightVNC
Nov 17 20:33:51 ubuntu vncserver[2439]: 17/11/19 20:33:50 Copyright (C) 1999 AT&T Laborato
Nov 17 20:33:51 ubuntu vncserver[2439]: 17/11/19 20:33:50 All Rights Reserved.
Nov 17 20:33:51 ubuntu vncserver[2439]: 17/11/19 20:33:50 See http://www.tightvnc.com/ for
Nov 17 20:33:51 ubuntu vncserver[2439]: 17/11/19 20:33:50 Desktop name 'X' (ubuntu:1)
Nov 17 20:33:51 ubuntu vncserver[2439]: 17/11/19 20:33:50 Protocol versions supported: 3.3
Nov 17 20:33:51 ubuntu vncserver[2439]: 17/11/19 20:33:50 Listening for VNC connections on
Nov 17 20:33:51 ubuntu vncserver[2439]: Fatal server error:
Nov 17 20:33:51 ubuntu vncserver[2439]: Couldn't add screen
makem@ubuntu:~$  - 

```

```

sudo nano ~/.vnc/xstartup

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
#unset DBUS_SESSION_BUS_ADDRESS

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
#export XKL_XMODMAP_DISABLE=1
#/etc/X11/Xsession
autocutsel -fork
startxfce4 &

```

The server starts correctly if I then enter the 'vncserver' command.

---

