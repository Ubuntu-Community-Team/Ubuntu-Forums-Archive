---
title: "Running long script at shutdown before network and docker go down"
date: 2018-12-01
forum: General Help
---

### Post by Panagiotis_Atmatzidis on 2018-12-01
Hi,

I have a python script which I need to run at shutdown. The script depends on network being up and docker daemon running. I'm using systemd on ubuntu 18.04, so I came up with this systemd service:

```
[Unit]
Description=pythonscript
Wants=docker.service
After=docker.service network-online.target


[Service]
Type=oneshot
RemainAfterExit=true
ExecStart=/bin/true
ExecStop=/opt/myfiles/sbin/pythonscript


[Install]
WantedBy=multi-user.target
```

The script normally takes anywhere from 30s to 90s to complete. What happens in my case is that the script runs but docker goes down before the script completes the run.

Ideas, thoughts welcome! 

Thanks for your time!

---

### Post by TheFu on 2018-12-03
Sometimes the easiest answer is to write a little script that you always use to shutdown.

Is docker automatically started by systemd?  If so, make the WantdBy use the docker.target

---

