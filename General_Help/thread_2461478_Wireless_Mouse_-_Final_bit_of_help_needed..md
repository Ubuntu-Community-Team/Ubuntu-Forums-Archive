---
title: "Wireless Mouse - Final bit of help needed."
date: 2021-05-01
forum: General Help
---

### Post by speartip on 2021-05-01
So my Logitech Wireless Mouse works fine, except, if I Suspend. Then the mouse wakes up the computer, but thereafter is dead. I found the problem was to disable power wake up. So if I run in a terminal:
```
[FONT=Carlito][COLOR=#000000]echo [/COLOR][/FONT][FONT=Carlito][COLOR=#000000][FONT=Carlito][FONT=Carlito]disabled[/FONT][FONT=Carlito] > /sys/bus/usb/devices/[/FONT][FONT=Carlito]1-1.3[/FONT][FONT=Carlito]/power/wakeup[/FONT][/FONT][/COLOR][/FONT]
``` 1-1.3 being the mouse, everything works fine. The problem is that this setting isn't permanent, I lose it at every reboot and have to do it again. So how do I make it a permanent setting?

---

### Post by Xian on 2021-05-02
You can create/enable/start a system services file in /etc/systemd/system/<file_name>.service

Similar could be done from a .bashrc file but it's messier an less secure.

For example:

```
[Unit]
Description=Disables power wakeup
After=network.target
StartLimitIntervalSec=0


[Service]
Type=simple
Restart=always
RestartSec=1
User=root
ExecStart=/usr/bin/sh -c "echo 'disabled' > /sys/bus/usb/devices/1-1.3/power/wakeup"


[Install]
WantedBy=multi-user.target
```

---

### Post by speartip on 2021-05-02
Thanks Xian. I tried your example, but power/wakeup is still enabled after a reboot. The code in my 1st post only works after "sudo su" & requires a password. Whether that's relevant I don't know. Also your example file, will it need making executable before copying to etc/systemd/system/ or not?

---

### Post by dinkidonk on 2021-05-02
Did you enable the service? If you named the service "nomouse.service" and stored it in "/etc/systemd/system/", then try to run "systemctl status nomouse". If the service shows up as "disabled", enable it with "sudo systemctl enable nomouse" and either reboot or start it with "sudo systemctl start nomouse". Run the "status" command to check if the service did what it should. You may also want to replace "Type=simple" with "Type=oneshot".

---

### Post by speartip on 2021-05-02
Thank you both. You've made my day. That's what I needed to do, run "[COLOR=#000000]sudo systemctl enable nomouse" first. Now my wireless mouse works as it should. Thanks again.[/COLOR]

---

