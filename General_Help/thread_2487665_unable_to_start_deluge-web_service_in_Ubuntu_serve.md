---
title: "unable to start deluge-web service in Ubuntu server"
date: 2023-06-12
forum: General Help
---

### Post by g-phanindra on 2023-06-12
i created the Deluge web interface service by using:
```
[Unit]
Description=Deluge Web Interface
After=network-online.target deluged.service
Wants=deluged.service

[Service]
Type=simple
User=gphan
Group=gphan
UMask=027
ExecStart=/usr/bin/deluge-web
Restart=on-failure

[Install]
WantedBy=multi-user.target

```

After reboot the web interface is not started;i have to manually start the web interface using
```
deluge-web -f

```when i check status using
```
sudo systemctl status deluge-web 

```it says web interface is deactivate
```
&#9675; deluge-web.service - Deluge Web Interface
     Loaded: loaded (/etc/systemd/system/deluge-web.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Mon 2023-06-12 01:38:32 UTC; 40s ago
    Process: 681 ExecStart=/usr/bin/deluge-web (code=exited, status=0/SUCCESS)
   Main PID: 681 (code=exited, status=0/SUCCESS)
        CPU: 638ms

Jun 12 01:38:30 point systemd[1]: Started Deluge Web Interface.
Jun 12 01:38:32 point systemd[1]: deluge-web.service: Deactivated successfully.



```

---

### Post by ActionParsnip on 2023-06-12
Then wouldn't your
```

ExecStart=/usr/bin/deluge-web

```
Need to be
```

ExecStart=/usr/bin/deluge-web -f

```

---

### Post by ActionParsnip on 2023-06-12
This may help
[https://deluge.readthedocs.io/en/latest/how-to/systemd-service.html](https://deluge.readthedocs.io/en/latest/how-to/systemd-service.html)

---

