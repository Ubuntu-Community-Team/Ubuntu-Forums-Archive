---
title: "Run service as AD user Ubuntu 16.04"
date: 2017-08-01
forum: General Help
---

### Post by yuljk2 on 2017-08-01
Hi guys - I have a Ubuntu 16.04 joined to my AD domain - AD user has been added to sudoers file.

I'd like to create a systemd service and run it as an AD user - is this possible?

Current systemd service looks like the following:-

```
[Unit]Description=Serviio Media Server
After=syslog.target local-fs.target network.target


[Service]
Type=simple
User=dlna
ExecStart=/opt/serviio/bin/serviio.sh
ExecStop=/opt/serviio/bin/serviio.sh -stop
KillMode=none
Restart=on-abort


[Install]
WantedBy=multi-user.target



```

Many thanks

---

