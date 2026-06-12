---
title: "xringd (ring detection daemon) config or params issue"
date: 2013-09-25
forum: General Help
---

### Post by Tom_Estat on 2013-09-25
Hello,

Distribution : lubuntu 13.04 up-to-date.

I would like to use xringd to launch /usr/local/bin/ring.sh

I tried to launch it in daemon and in debug mode, with and without parameters, and i systematically get a syntax error message "usage:..." (although my parameters and config file both seem correct to me) :

```
fg@gateway:~$ xringd -n
xringd: config file /etc/xringd.conf -> syntax ok

fg@gateway:~$ xringd -d -a /usr/local/bin/ring.sh -m /dev/ttyACM0 
xringd: needs Linux 1.3.48+, 16xx0 uart
xringd version 1.20 - by A. Haritsis (ah@doc.ic.ac.uk)
usage: xringd [-a rngcmd] [-c cfgfile] [-d] [-h] [-i ignore_msec] [-l loglevel]
              [-m modem_dev] [-e] [-n] [-t initime] [modem_dev]

fg@gateway:~$ xringd
xringd: needs Linux 1.3.48+, 16xx0 uart
xringd version 1.20 - by A. Haritsis (ah@doc.ic.ac.uk)
usage: xringd [-a rngcmd] [-c cfgfile] [-d] [-h] [-i ignore_msec] [-l loglevel]
              [-m modem_dev] [-e] [-n] [-t initime] [modem_dev]
```
I also tried to launch it with the init script, but then i dont get any error message, nothing from xringd in syslog and the xringd daemon does not run :
```
fg@gateway:~$ sudo /etc/init.d/xringd start
[sudo] password for fg: 
Starting Phone line monitor: xringd.
fg@gateway:~$ ps aux | grep xringd
fg        7495  0.0  0.0   5672   844 pts/1    S+   12:07   0:00 grep --color=auto xringd
fg@gateway:~$

```
Perms on /usr/local/bin/ring.sh are 755 :
```
fg@gateway:~$ ls -l /usr/local/bin/ring.sh 
-rwxr-xr-x 1 root root 62 sep 25 11:43 /usr/local/bin/ring.sh
fg@gateway:~$ cat /usr/local/bin/ring.sh 
#!/bin/sh
/usr/bin/mpg321 /data/fg-data/telephone-ring-2.mp3
```

Here is my xringd.conf config file : [http://pastebin.com/Y9nDVQcf](http://pastebin.com/Y9nDVQcf)

Could somebody please help me understanding/correcting my mistake ?

Thank you :)

---

