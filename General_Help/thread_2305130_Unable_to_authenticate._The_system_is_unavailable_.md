---
title: "Unable to authenticate. The system is unavailable due..... - Error message"
date: 2015-12-03
forum: General Help
---

### Post by janeku2 on 2015-12-03
Hello ,
Suddenly I faced strange error on my Ubuntu 14.04 LTS (latest upgrade) with one error:
" Unable to authenticate. The system is unavailable due to urgent system maintenance."

It is repetitive error so I tried to see what log files are made for this error and in var/log/
3 log files are filled with data showing this error: ufw.log , syslog and kern.log

Last 2 error logs of these log files are:

From ufw.log:
```
Dec  3 06:30:16 petrika-MS-7388 kernel: [ 1217.084802] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:86:39:55:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=5607 PROTO=2 
Dec  3 06:30:31 petrika-MS-7388 kernel: [ 1232.098030] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:86:39:55:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=5615 PROTO=2
``` 

From syslog:
```
Dec  3 06:31:01 petrika-MS-7388 kernel: [ 1262.124483] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:86:39:55:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=5657 PROTO=2 
Dec  3 06:31:16 petrika-MS-7388 kernel: [ 1277.137653] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:86:39:55:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=5660 PROTO=2 

```
From kern.log:
```
Dec  3 06:31:16 petrika-MS-7388 kernel: [ 1277.137653] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:86:39:55:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=5660 PROTO=2 
Dec  3 06:31:31 petrika-MS-7388 kernel: [ 1292.150880] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:e8:94:f6:86:39:55:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=5671 PROTO=2 

```
What is this error about and how can I fix this issue and stop this error log showing ?

Regards,

---

### Post by Bucky Ball on 2015-12-03
Run these three commands one after the other and report any and all errors:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

How did you install UFW? From the Software Centre?

---

### Post by janeku2 on 2015-12-03
Hello,
I made suggested updates and upgrades and there is no error.
UFW (Firewall) is installed with Software center.

Regards,

---

### Post by janeku2 on 2015-12-03
I am wondering why it is happening. It is no first time to see this, it usually happened if I lost my internet conenction and there is possible update.
If I lost internet I had to connect via usb tethering on my phone and make update to make everything work.
What is so dependable of internet connection and what needs to make login to something ?
Regards,

---

