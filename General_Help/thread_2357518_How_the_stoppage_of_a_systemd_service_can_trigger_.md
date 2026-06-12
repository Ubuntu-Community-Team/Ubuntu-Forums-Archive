---
title: "How the stoppage of a systemd service can trigger the stoppage of different one?"
date: 2017-04-03
forum: General Help
---

### Post by dk1979 on 2017-04-03
I'm creating a systemd service let's call it B on Ubuntu 16.04 which I'd like on every boot to start after a specific service called A and then run a specific script. So far I've created the service unit file which consists of the following fields:

```
[Unit]
Description=B
After=A.service


[Service]
ExecStart=/opt/B.sh


[Install]
WantedBy=multi-user.target

``` 

Furthermore I'd like the stoppage of service A to trigger the stoppage of service B. I assume that the following command on A service unit file will do the job:

```
ExecStop=systemctl stop A.service

```

However is there another way supposedly someone does not want to change the A service unit file?

---

