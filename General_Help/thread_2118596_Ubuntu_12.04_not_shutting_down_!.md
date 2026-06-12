---
title: "Ubuntu 12.04 not shutting down !"
date: 2013-02-21
forum: General Help
---

### Post by Akasashasha on 2013-02-21
Hello,

when I close my session and click on shutdown nothing happen ... what's the problem ?
everything has been installed properly with partitions, etc ... 

here are some details on my config :
* AMD Athlon(tm) II X3 450 Processor × 3 
* VESA : RS780
* 64bits
*8go ram
* 1000Go

thanks for your help ...

---

### Post by ali abry on 2013-02-21
try terminal ways.
```
 sudo shutdown -p now
```
and if you didn't succeed check log files :
/var/log/syslog ...

---

### Post by gifford on 2013-02-21
Are you getting nothing? Or do you get the beginning of the lines indicating it is starting to shut down?

---

### Post by Akasashasha on 2013-02-22
> **gifford said:**
> Are you getting nothing? Or do you get the beginning of the lines indicating it is starting to shut down?

getting nothing, just stay on the same page  ... I tried to reopen and reclose each sessions but this is also not working ... I saw some similar problems in other threads but did not found a solution.

thank you

---

### Post by dino99 on 2013-02-22
is your system fully updated ?
do you get errors logged ? (.xsession-errors & /var/log/)

to get the verbose mode, and be able to see the booting/closing comments:

```
sudo gedit /etc/default/grub
```

--> remove "quiet splash", then :
```
sudo update-grub
```

before trying to shut down again, run:

```
sudo apt-get install --reinstall ubuntu-desktop

``````
sudo dpkg-reconfigure -phigh -a
```
(can take a while, dont stop it yourself)

if you still cant logout/shutdown, then force power off button, and glance at the verbose mode on next cold boot

---

