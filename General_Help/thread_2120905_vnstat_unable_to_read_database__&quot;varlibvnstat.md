---
title: "vnstat: unable to read database  &quot;/var/lib/vnstat/eth1"
date: 2013-02-27
forum: General Help
---

### Post by t0p on 2013-02-27
Just started a 3G/HSPA dongle, Huawei E3231. It's a pay-as-you-go deal, so I want to keep track of how much data transfer I'm getting through. Thing is, Ubuntu is recognising the dongle as interface eth1, but it's not created a eth1 database

```

t0p@mars:~$ vnstat -i eth1
Error: Unable to read database "/var/lib/vnstat/eth1".
t0p@mars:~$ ls /var/lib/vnstat/eth1
ls: cannot access /var/lib/vnstat/eth1: No such file or directory
t0p@mars:~$

```

The only interfaces it seems to see are eth0, usb0 and wlan0:

```
t0p@mars:~$ ls /var/lib/vnstat
eth0  usb0  wlan0
t0p@mars:~$

```

How do I make it see eth1? Alternatively, is there another tool I can use to keep track of data transfer?

Cheers.

---

### Post by sbjaved on 2013-09-22
Try **sudo vnstat -u -i eth1**. This will create a new eth1 database. Then run **vnstat -l -i eth1** to see if its picking up data for eth1 in realtime.

---

