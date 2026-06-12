---
title: "Systemd unable to start a personal unit"
date: 2015-09-01
forum: General Help
---

### Post by odror on 2015-09-01
I have created the following unit in ~/.config/systemd/user/onedrive.service

```
[Unit]
Description=Enable onedrive connection on boot
After=network.target

[Service]
ExecStart=/usr/local/bin/onedrive-d start
ExecReload=/usr/local/bin/onedrive-d restart
ExecStop=/usr/local/bin/onedrive-d stop  
```

When I type
systemctl --user status onedrive
I get the following error:

```
$ systemctl --user status onedrive
&#9679; onedrive.service - Enable onedrive connection on boot
   Loaded: loaded (/home/myhome/.config/systemd/user/onedrive.service; static; vendor preset: enabled)
   Active: inactive (dead)

Sep 01 15:34:47 mysystem systemd[20127]: [/home/myhome/.config/systemd/user/onedrive.service:1] Unknown section 'unit'. Ignoring.
Sep 01 15:34:47 mysystem systemd[20127]: [/home/myhome/.config/systemd/user/onedrive.service:4] Unknown section 'service'. Ignoring.
Sep 01 15:34:47 mysystem systemd[20127]: onedrive.service lacks both ExecStart= and ExecStop= setting. Refusing.
Sep 01 15:35:08 mysystem systemd[20127]: [/home/myhome/.config/systemd/user/onedrive.service:1] Unknown section 'unit'. Ignoring.
Sep 01 15:35:08 mysystem systemd[20127]: [/home/myhome/.config/systemd/user/onedrive.service:4] Unknown section 'service'. Ignoring.
Sep 01 15:35:08 mysystem systemd[20127]: onedrive.service lacks both ExecStart= and ExecStop= setting. Refusing.

```

Why I get this error?

Thanks for any help.

---

