---
title: "Systemd service possible without After= Before= nor WantedBy= ?"
date: 2020-06-04
forum: General Help
---

### Post by desconocido on 2020-06-04
I have a service which I only want to run once, at boot time. But it gets called whenever Bluetooth is turned on. Could I stop this by removing some or all of the references to other targets and services?

This is the current version of the service:

```
[Unit]
Description=Service to always turn bluetooth off at system start time
After=NetworkManager.service
Before=network-online.target

[Service]
Type=oneshot
Restart=no
ExecStart=/usr/local/bin/turn-bluetooth-off.sh

[Install]
WantedBy=default.target

```

---

### Post by izznogooood on 2020-06-05
Something is triggering your service.

You could rename the file and:
"systemctl enable NEW_SERVICE_NAME.service" and what ever tries to trigger it wont find it and it would only start once.

Dont forget to "systemctl disable OLD_FILE_NAME.service" first.

The propper way though would be to figure out whats calling it in the first place ;)

---

