---
title: "change TTL value"
date: 2021-01-05
forum: General Help
---

### Post by vpn9601 on 2021-01-05
[SIZE=4]
[/SIZE]
[SIZE=4][COLOR=#202124][FONT=arial][SIZE=4]Good afternoon friends ! It is necessary to change the Time to live (TTL) value - 64, write the new value 65. Used the following recommendations -```
sudo echo net.ipv4.ip_default_ttl = 65 >> /etc/sysctl.conf
sudo sysctl --system
```However, after that, the wi-fi adapter stopped working, displays the message "cannot connect" This problem appears exactly after the execution of these commands. On old version 18.04 this worked. How to solve this problem?[/SIZE]

[/FONT][/COLOR][/SIZE][SIZE=3]Linux rvr-p5k 5.4.0-42-generic #46-Ubuntu SMP Fri Jul 10 00:24:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
[/SIZE]No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:        20.04
Codename:       focal

---

