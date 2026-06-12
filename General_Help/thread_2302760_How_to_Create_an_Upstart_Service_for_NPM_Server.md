---
title: "How to Create an Upstart Service for NPM Server"
date: 2015-11-13
forum: General Help
---

### Post by tehtotalpwnage on 2015-11-13
I'm currently running Ubuntu 14.04 and I have a NPM application that runs as a server that I would start and stop with the commands:

sudo npm start | sudo npm stop

How would I convert this into an upstart script so that I can manage my NPM application as a service?

---

### Post by xsnake_ on 2015-11-13
You could try something like this:

[COLOR=#000000][FONT=Consolas]Create /etc/systemd/system/npm.service

[/FONT][/COLOR]```
[COLOR=black][FONT=Consolas][Unit]
[/FONT][/COLOR][COLOR=black][FONT=Consolas]Description=NPM Daemon
[/FONT][/COLOR][COLOR=black][FONT=Consolas]
[Install]
[/FONT][/COLOR][COLOR=black][FONT=Consolas]WantedBy=multi-user.target

[/FONT][/COLOR][COLOR=black][FONT=Consolas][Service]
[/FONT][/COLOR][COLOR=black][FONT=Consolas]Type=simple
[/FONT][/COLOR][COLOR=black][FONT=Consolas]PrivateTmp=true[/FONT][/COLOR][COLOR=black][FONT=Consolas]
[/FONT][/COLOR][COLOR=black][FONT=Consolas]ExecStart=/usr/bin/npm --whatever-options
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Consolas]

Enable the service at boot time:
[/FONT][/COLOR]```
sudo [COLOR=#000000][FONT=Consolas]systemctl enable npm.service[/FONT][/COLOR]
```[COLOR=#000000][FONT=Consolas]

[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]Start/Stop the service using:
[/FONT][/COLOR]```
sudo [COLOR=#000000][FONT=Consolas]systemctl start npm.service[/FONT][/COLOR]
```[COLOR=#000000][FONT=Consolas]

Regards,
Carl[/FONT][/COLOR]

---

### Post by tehtotalpwnage on 2015-11-14
Version for Upstart? I'm still running on Ubuntu 14.04, which hasn't implemented systemd.

---

### Post by tehtotalpwnage on 2015-11-29
bump

---

