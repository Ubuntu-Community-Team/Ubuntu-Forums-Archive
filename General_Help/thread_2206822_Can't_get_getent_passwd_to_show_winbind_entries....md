---
title: "Can't get getent passwd to show winbind entries..."
date: 2014-02-21
forum: General Help
---

### Post by Contoured_Solution on 2014-02-21
So, I can poll winbind entries when I run wbinfo -u. However, getent passwd gets nothing but local users. Here's my smb.conf file:

```

[global]
        allow trusted domains = Yes
        disable spoolss = yes
        dns proxy = No
        encrypt passwords = Yes
        idmap backend = rid:SOMEDOMAIN=10000-20000
        idmap gid = 10000-20000
        idmap uid = 10000-20000
        load printers = No
        log level = 0
        map to guest = Never
        max log size = 50
        os level = 10
        password server = SOMEIPADDRESS
        realm = SOMEDOMAIN.LOCAL
        security = ads
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
        stat cache = No
        unix charset = UTF8
        winbind cache time = 300
        winbind enum groups = Yes
        winbind enum users = Yes
        winbind gid = 10000-20000
        winbind nested groups = Yes
        winbind uid = 10000-20000
        winbind use default domain = No
        workgroup = SOMEDOMAIN
    log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
    encrypt passwords = true
        printing = cups
        printcap name = cups

```

Here's my nss_switch.conf

```
passwd:         compat winbind
group:          compat winbind
shadow:         compat winbind


hosts:  files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis



```
Poking around, I can't seem to find nss_winbind.so.1 or nss_winbind.so anywhere. Isn't this file needed?

If I run find / -name *nss_winbind* I get the following:

```
/usr/share/doc/samba-doc/examples/nss/nss_winbind.h
/usr/share/doc/samba-doc/examples/nss/nss_winbind.c.gz

```


Can someone help me out? Maybe this nss_winbind.so.1 thing is a dead end, but I have not been able to find anything else and this is the second installation of Samba I've tried. Any ideas?

---

### Post by Contoured_Solution on 2014-02-26
Figured it out. The winbind NSS library no longer comes with winbind, it seems. You need to run this:

apt-get install libnss-winbind

In order to get it to work.

---

