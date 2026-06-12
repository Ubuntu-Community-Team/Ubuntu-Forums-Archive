---
title: "issues with lighttpd"
date: 2019-01-09
forum: General Help
---

### Post by classified on 2019-01-09
hi all sorry if wrong place but i need some help i am trying to get xampp working  but it will not start ot says another server is runnig i found out its lighttpd but that is not installed help text below from terminal if you can pick more out of it 


midnight@torchwood-lap:~$ sudo lsof -i :80
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
lighttpd         1241 root      4u     IPv4  29855      0t0          TCP     *:http (LISTEN)
midnight@torchwood-lap:~$ sudo apt-get purge --auto-remove lighttpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'lighttpd' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 33 not to upgrade.
midnight@torchwood-lap:~$ sudo lsof -i :80
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
lighttpd         1241 root      4u     IPv4  29855      0t0           TCP      *:http (LISTEN)
midnight@torchwood-lap:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 7.3.0-0...
XAMPP: Starting Apache...fail.
XAMPP:  Another web server is already running.
XAMPP: Starting MySQL...already running.
XAMPP: Starting ProFTPD...already running.
midnight@torchwood-lap:~$ sudo /opt/lampp/lampp stop
Stopping XAMPP for Linux 7.3.0-0...
XAMPP: Stopping Apache...not running.
XAMPP: Stopping MySQL...ok.
XAMPP: Stopping ProFTPD...ok.
midnight@torchwood-lap:~$ sudo /opt/lampp/lampp start
Starting XAMPP for Linux 7.3.0-0...
XAMPP: Starting Apache...fail.
XAMPP:  Another web server is already running.
XAMPP: Starting MySQL...ok.
XAMPP: Starting ProFTPD...ok.

---

### Post by oldos2er on 2019-01-09
Support,  not Chat; moved to General Help.

---

