---
title: "Remote Rsyslog and filtering issues"
date: 2013-10-02
forum: General Help
---

### Post by szpuni2 on 2013-10-02
Hello,

I'm trying to setup and remote rsyslog server between centos and ubuntu 12.04 and I have huge problems with filter in rsyslog.

Problem is that most of things from documentation do not work (like most of If statements). 
In receiving ryslog I have:

```
if $fromhost-ip startswith '192.168.170.20' and $programname == 'asterisk' then /var/log/asterisk.log
& ~


if $fromhost-ip startswith '192.168.170.20' and $programname != 'asterisk' then /var/www/logs/kamailio.log
& ~

```


This was working fine in version 11.04 and my logs where going to correct locations. Unfortunate in 12.04 version this statement do not work at all and actuall causing rsyslog to not log anything from remote host.

Only one I got to work is when I use:

```
if $hostname == 'remote_hostname' then /var/log/kamailio.log
& ~

```
But I need a bit more filtering options to work. I need to split logs to different files and not just filter it by hostname (btw if I use ip address of that host rather than hostname filter do not work at all)

After a while I have found templates and other filtering options but still I can only filter those messages by ip address:
```

$template KamFile,"/var/log/kamailio.log"
:fromhost-ip, isequal, "192.168.170.20" ?KamFile
:fromhost-ip, isequal, "192.168.170.20" ~

```




Do not understand why i need second fromhost-ip but this is only way to get it working.
This would suite me if I could use additional filtering parameters but manual do not mention anything about adding additional parameters and using something like:

```
 $template KamFile,"/var/log/kamailio.log"
:programname, contains, "kamailio" ?KamFile
:programname, contains, "kamailio" ~

```
do not work at all and all logs are being sent to main /var/log/syslog file instead.

Example log:

```
Oct  2 14:22:18 vn3ic001 /usr/sbin/kamailio[26643]: NOTICE: <core> [dprint.c:123]: #012Src IP:............
Oct  2 14:22:18 vn3ic001 /usr/sbin/kamailio[26643]: NOTICE: <core> [dprint.c:123]: #012Src IP:............
```

Any ideas how to get that filtering to work?
Anybody had same or similar issues with rsyslog filtering messages?

---

### Post by szpuni2 on 2013-10-03
Nobody had similar issues?

---

