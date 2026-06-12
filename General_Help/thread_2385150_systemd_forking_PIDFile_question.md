---
title: "systemd forking PIDFile question"
date: 2018-02-16
forum: General Help
---

### Post by Steve Goodey on 2018-02-16
I have a PC running Mythbuntu which has an LCD which I had a bit of a struggle getting going under systemd. However using
 Type=forking it is now working fine. However reading the man page for systemd.service is says that it is recommended 
to use PIDFile. I have tried adding PIDFile=/run/LCDd.pid but this causes an error message:-

```
LCDd.service - LCDd
   Loaded: loaded (/etc/systemd/system/LCDd.service; enabled; vendor preset: enabled)
   Active: activating (start) since Tue 2018-02-13 09:49:03 GMT; 1min 8s ago
  Process: 2485 ExecStart=/usr/sbin/LCDd -c /home/steve/lcd/LCDd.conf (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/LCDd.service
           &#9492;&#9472;2487 /usr/sbin/LCDd -c /home/steve/lcd/LCDd.conf

Feb 13 09:49:03 mythbuntu systemd[1]: Starting LCDd...
Feb 13 09:49:03 mythbuntu systemd[1]: LCDd.service: PID file /run/LCDd.pid not readable (yet?) after start: No such file or directory
steve@mythbuntu:~$  
```

I have tried creating LCDd.pid in /run with root:root but get the same. How is the pid file generated?

```

LCDd.service

[Unit]
Description=LCDd
After=multi-user.target

[Service]
Type=forking
PIDFile=/run/LCDd.pid
ExecStart=/usr/sbin/LCDd -c /home/steve/lcd/LCDd.conf
TimeoutStopSec=1s
Restart=on-failure
RestartSec=5
StartLimitInterval=30
StartLimitBurst=5

[Install]
WantedBy=multi-user.target
```

LCDd.conf
```

## This file was written by cme command.
## You can run 'cme edit lcdproc' to modify this file.
## You may also modify the content of this file with your favorite editor.


[server]
DriverPath=/home/steve/lcd/
Driver=vlsys_m428
NextScreenKey=Right
PrevScreenKey=Left
ReportToSyslog=yes
ToggleRotateKey=Enter
ServerScreen=no

Bind=127.0.0.1
Port=13666
User=nobody
Hello="Mythbuntu"
WaitTime=5

[menu]
DownKey=Down
EnterKey=Enter
MenuKey=Escape
UpKey=Up

[vlsys_m428]
Device=/dev/ttyUSB0

LCDd.conf (END)
```

---

