---
title: "tftpd-hpa Doesn't Show in Process List"
date: 2012-11-21
forum: General Help
---

### Post by socialdtk on 2012-11-21
After rebooting my system tftpd-hpa does not show up in my process list:

**ps aux | grep tftp | grep -v grep**

When attempting to start the service I get the following message:

**sudo service tftpd-hpa start**
start: Job is already running: tftpd-hpa

After restarting the service it shows up in the process list:

**sudo service tftpd-hpa restart**
tftpd-hpa stop/waiting
tftpd-hpa start/running, process 1690

**ps aux | grep tftp | grep -v grep**
root      1690  0.0  0.0   2684   124 ?        Ss   22:22   0:00 /usr/sbin/in.tftpd --listen --user tftp --address 0.0.0.0:69 --secure /var/lib/tftpboot

---

### Post by socialdtk on 2012-11-21
I created a copy of /var/log/boot.log and restarted the system. I then compared the two files:

**diff boot.log boot.log.test | grep tftp**
>  * Starting tftp-hpa server                                                  [ OK ]

**ps aux | grep tftp | grep -v grep**

---

### Post by socialdtk on 2012-11-22
I tried completely deleting tftpd-hpa and all of its configuration files and am still experiencing the same problem. Any ideas?

---

### Post by qdwh on 2013-02-07
I got the exactly same issue. I'm using Ubuntu12.04 LTS desktop.

---

