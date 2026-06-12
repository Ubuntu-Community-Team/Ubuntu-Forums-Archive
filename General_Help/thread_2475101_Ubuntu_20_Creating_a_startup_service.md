---
title: "Ubuntu 20: Creating a startup service"
date: 2022-05-16
forum: General Help
---

### Post by zee-bra on 2022-05-16
[COLOR=#232629][FONT=-apple-system]I have an app which I want to start when the server starts.

I also want the app to automatically restart if it ever crashed and stops.

My understanding is that I need to setup a systemd service for this.

This is what I have done so far:[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
**/etc/systemd/system/multi-user.target.wants/userapp.service**

[/FONT][/COLOR]
```
[Unit]
Description=User App
After=network.target

[Service]
User=user
WorkingDirectory=/home/user
ExecStart=/home/user/start.sh
KillMode=process
StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=what
Restart=on-failure
RestartSec=60

[Install]
WantedBy=multi-user.target

```

[COLOR=#232629][FONT=-apple-system]**start.sh**

[/FONT][/COLOR]
```
#!/bin/bash
echo "Starting UserApp" | logger
./userapp

```

[COLOR=#232629][FONT=-apple-system]The problem is the service starts, no errors, then the service immediately stops, and the app. The start.sh and userapp are both chmod +x 755

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Can anyone help me understand whats wrong?[/FONT][/COLOR]

---

### Post by TheFu on 2022-05-17
GUI programs cannot be started without a user session as the parent.
Is this program a daemon?

---

### Post by ActionParsnip on 2022-05-17
Also the pwd of the command is relevant in your script so use absolute paths rather than the dot slash notation.

---

### Post by TheFu on 2022-05-17
> **ActionParsnip said:**
> Also the pwd of the command is relevant in your script so use absolute paths rather than the dot slash notation.

Good catch.  This assumes any script and programs called by the script can be run from any directory.

Running daemons from a user's HOME isn't usually done. There are many reasons why this would be a bad idea. All sorts of things can get in the way. Best to put system daemons in system locations.

To start a user's daemon at reboot (non-GUI), I'd probably use the crontab with an "@reboot" time spec.
To start a GUI program for a user, that has to wait until they login. Most window managers or DEs have a way to specify that a specific program be automatically started at login.  The _Ubuntu Desktop Guide_ has that documented.

---

