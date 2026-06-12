---
title: "No Eligible Servers"
date: 2024-11-09
forum: General Help
---

### Post by coconut-aero on 2024-11-09
```

sudo ntpdate ntp.tuna.tsinghua.edu.cn
ntpdig: no eligible servers

```

My machine installed multiple systems, including Ubuntu 24.04 and Windows 11. But every time I reboot my laptop it turns wrong time, seems to be -8h in Windows but +8h in Ubuntu.

Every time I need to sync the time with the time server nearby(ntp.tuna.tsinghua.edu.cn), however I got these error messages.

I am new to Ubuntu. How can I solve it?

---

### Post by yancek on 2024-11-09
The link below discusses obtaining system time and setting it on Ubuntu.  If you have multiple systems installed, they should all be set to either UTC or local time or you will see warning/error messages on boot.

[https://ubuntu.com/core/docs/system-time](https://ubuntu.com/core/docs/system-time)

---

### Post by flipchip8827 on 2024-11-09
You configure your machines to initially connected to once you've  imitated the installation. The installation wizard should at least attempt to make an educated guess on your local time zone based upon your routers WAN ip address which is typically a pretty good method by which to determine the client systems time. In certain casses like your machine being behind multiple firewalls or other IP address based filtration and access control points.

---

