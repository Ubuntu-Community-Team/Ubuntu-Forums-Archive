---
title: "Fresh install of Ubuntu 16.04 and Plex Media Server"
date: 2017-01-13
forum: General Help
---

### Post by john.lynch on 2017-01-13
I'm new to Linux and have tried to install PlexMediaServer, however it's not working. Here's the output I'm getting when I try to start the service:
```
jbpc@Claudius:~$ sudo systemctl enable plexmediaserver.service
[sudo] password for jbpc: 
jbpc@Claudius:~$ sudo systemctl start plexmediaserver.service
Job for plexmediaserver.service failed because the control process exited with error code. See "systemctl status plexmediaserver.service" and "journalctl -xe" for details.
jbpc@Claudius:~$ sudo systemctl status plexmediaserver.service
&#9679; plexmediaserver.service - Plex Media Server for Linux
   Loaded: loaded (/etc/systemd/system/plexmediaserver.service; enabled; vendor 
   Active: activating (auto-restart) (Result: exit-code) since Fri 2017-01-13 16
  Process: 12789 ExecStartPre=/bin/sh -c /usr/bin/test -d "${PLEX_MEDIA_SERVER_A

Jan 13 16:07:30 Claudius systemd[1]: Failed to start Plex Media Server for Linux
Jan 13 16:07:30 Claudius systemd[1]: plexmediaserver.service: Unit entered faile
Jan 13 16:07:30 Claudius systemd[1]: plexmediaserver.service: Failed with result
```Any ideas? I've tried to uninstall and reinstall a couple of times now but I'm not getting anywhere.

jbpc@Claudius:~$

---

### Post by David D. on 2017-01-13
I use the following command in terminal to start Plex Media Server:
start_pms

---

### Post by john.lynch on 2017-01-13
Well that's embarrassing. Thankyou.

Is there a way to get this to run automatically on computer launch?

---

