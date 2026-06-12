---
title: "Syslog Messages - Redirect"
date: 2014-10-07
forum: General Help
---

### Post by mcparty2 on 2014-10-07
Hi,

I have searched the forum for answers to this but I cannot see any so...

I have a syslog server on Ubuntu 12.04 LTS and near enough 200 devices sending syslog entries to it and I would like to split up the logs, for example:

From:
/var/log/syslog

 To:
/var/log/routers
/var/log/switches
/var/log/vmhosts

Is there an easy way to do this in the syslog.conf file? the man pages don't seem to address my query.

Many thanks

---

### Post by btindie on 2014-10-07
That's quite straightforward, you just need to know what you can filter on.

You can add files to /etc/rsyslog.d/ that define what to do with various messages based on conditions.

There's a couple of examples below but it depends on your setup as to how's best to filter them
```
:syslogfacility-text, isequal, "local5" /var/log/vmhosts
& ~

:syslogtag, startswith, "router" /var/log/routers
& ~

:msg, contains, "[SWITCH " /var/log/switches
& ~

:fromhost-ip, startswith, "192.168.5." /var/log/vmhosts
& ~

```

The '& ~' tells it to drop the packet after a successful match and don't process it any more.

Then restart rsyslog with "sudo restart rsyslogd".

For more examples take a look at the rsyslog documentation
[http://www.rsyslog.com/doc/rsyslog_conf_filter.html](http://www.rsyslog.com/doc/rsyslog_conf_filter.html)
[http://www.rsyslog.com/doc/property_replacer.html](http://www.rsyslog.com/doc/property_replacer.html)

And [RFC3164]("http://www.ietf.org/rfc/rfc3164.txt") if you need to brush up on syslog.

You'd also want to create the files beforehand with
```
for f in routers switches vmhosts; do sudo install -o syslog -g adm -m 0640 /dev/null /var/log/$f; done
```
This sets the correct permissions on the files.

Once that's all working, you'd also want to create a profile in /etc/logrotate.d/ to rotate those files, there's plenty in there that you can use as examples.

---

### Post by mcparty2 on 2014-10-07
btindie, 

That is an awesome response and very comprehensive. :smile:
I shall have a go tonight and I'll let you know how I get on.

Many many thanks

---

### Post by mcparty2 on 2014-10-07
Unfortunately this hasn't worked using the IP or the hostname, I have created the log file and set the permissions as suggested.
I have tried placing the following in the [FONT=Menlo]/etc/rsyslog.d/50-default.conf[/FONT] file:

```
[COLOR=#5330E1][FONT=Menlo][COLOR=#000000]:fromhost-ip, startswith, "10.10.10." /var/log/vmhosts[/COLOR][/FONT][/COLOR]
[COLOR=#5330E1][FONT=Menlo][COLOR=#000000]& ~[/COLOR][/FONT][/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#5330E1][FONT=Menlo][COLOR=#000000]:fromhost, startswith, "vmhost1.core" /var/log/vmhosts[/COLOR][/FONT][/COLOR]
[COLOR=#5330E1][FONT=Menlo][COLOR=#000000]& ~[/COLOR]

[/FONT][/COLOR]
```

I have gone through the links and tried setting the following in:

```
[FONT=Menlo]$template DynaFile,”/var/log/core/%HOSTNAME%.log”*.* -?DynaFile

[/FONT]

```

Either sets of config doesn't cause any errors upon restarting the demon. I shall continue to persevere - but is there anything I am doing wrong here?

---

### Post by Habitual on 2014-10-07
> **mcparty2 said:**
> I have a syslog server on Ubuntu 12.04 LTS  version of syslog?
I believe it's rsyslogd by default on 12.04? Anyone...?

```
rsyslogd -v
```

---

### Post by mcparty2 on 2014-10-08
Apparently it isn't installed:

```

root@syslog1: rsyslogd -v
The program 'rsyslogd' is currently not installed.  You can install it by typing:
apt-get install rsyslog

```

Though the directory exists, and when i restart rsyslogd, it starts ok

```

root@syslog1:/etc/rsyslog.d# ls -al
total 20
drwxr-xr-x  2 root root 4096 Oct  7 22:21 .
drwxr-xr-x 91 root root 4096 Oct  3 06:45 ..
-rw-r--r--  1 root root  311 Mar 17  2012 20-ufw.conf
-rw-r--r--  1 root root 1845 Oct  7 19:30 50-default.conf
-rw-r--r--  1 root root  242 Feb 20  2013 postfix.conf

```


```

root@syslog1:/etc/rsyslog.d# sudo service rsyslog restart
rsyslog stop/waiting
rsyslog start/running
root@syslog1:/etc/rsyslog.d# 

```

```

Oct  8 12:30:06 syslog1 kernel: [12766542.931413] init: rsyslog main process (20609) terminated with status 127
Oct  8 12:30:06 syslog1 kernel: [12766542.931445] init: rsyslog main process ended, respawning

```


I do seem to be using syslogd though

```

root@syslog1: syslogd -v
syslogd 1.5.0

```


Does this help?

Many thanks

---

### Post by btindie on 2014-10-08
> **mcparty2 said:**
> I have tried placing the following in the [FONT=Menlo]/etc/rsyslog.d/50-default.conf[/FONT] file:
You'd be better off creating a new file with a higher priority such as */etc/rsyslog.d/10-network.conf* and sticking your rules in there so they take priority over the default rules.

Otherwise the rules look fine. Just remember to restart rsyslog after you make the changes - sudo restart rsyslog

When testing, run tcpdump to see if you're actually getting any traffic:
```
tcpdump -i eth0 -s0 -n -v port 514
```

You can test it remotely by using the *logger* command. There's a bug in the current version, at least in Debian, that means it won't work correctly for network logging. There's a work around by passing "-u /tmp/ignored"
```
logger -u /tmp/ignored -n syslog.server.ip -t TAG -i Syslog Test
```


> **mcparty2 said:**
> Apparently it isn't installed:

```

root@syslog1: rsyslogd -v
The program 'rsyslogd' is currently not installed.  You can install it by typing:
apt-get install rsyslog

```

What's the output of
```
dpkg -l | grep syslog
initctl list | grep syslog
which rsyslogd

```

---

### Post by mcparty2 on 2014-10-08
Thanks for your response.

I have created a higher priority file 10-network.conf with the previously posted config (going for IP address to ensure there are no hidden DNS issues).
I am definately receiving connections and they are logging to the /var/log/syslog file. Here is an example of a packet recieved from the tcpdump:

```

15:42:21.937597 IP (tos 0x0, ttl 62, id 16979, offset 0, flags [none], proto UDP (17), length 111)
    10.10.11.35.2767 > 10.10.10.13.514: SYSLOG, length: 83
    Facility local4 (20), Severity alert (1)
    Msg: OCT 08 14:42:18: alert  : 1/1/1025: alarm_mgr: 01: 1:05 Minor DSL Up DSL line\0x0a

```

And my logger query suceeded:

```

Oct  8 15:51:45 100.65.6.136 TAG: - Syslog Test

```


Here is the output you requested:

```

root@syslog1:/etc/rsyslog.d# dpkg -l | grep syslog
rc  rsyslog                          5.8.6-1ubuntu8               reliable system and kernel logging daemon
root@syslog1:/etc/rsyslog.d# initctl list | grep syslog
rsyslog start/running
root@syslog1:/etc/rsyslog.d# which rsyslogd
root@syslog1:/etc/rsyslog.d# 

```

Kind regards

---

### Post by btindie on 2014-10-08
It looks like you may have some other syslog server installed instead of rsyslog, possibly sysklogd ? You should be able to identify it with
```
dpkg -l | awk '$2 ~ /sys[a-z]*log/ {print $0}'
```
and to see the process running
```
ps ax | awk '$5 ~ /sys[a-z]*log/ {print $0}'
```

From *man dpkg-query* it would seem that rsyslog has been removed, but the configuration files haven't. Hence the 'rc' status in the dpkg output.

You'll need to install rsyslog
```
sudo apt-get install rsyslog
```

And remove the other one
```
sudo apt-get remove --purge sysklogd
```
If sysklogd is the other package that's installed.

---

### Post by mcparty2 on 2014-10-09
Yep, looks like sysklogd is running. :)
I shall do the swap over to rsyslog in that case.

Thank you again for your help. I'll report back soon.

---

### Post by mcparty2 on 2014-10-10
Hurrah, the split is working.
My Syslog file is now showing core routers & switches:

```

Oct   9 14:47:53 pe1.core 7913: Oct  9 13:47:52.361 GMT: %BGP-5-ADJCHANGE:  neighbor 100.80.64.152 vpn vrf nyccspare1-12 Down BGP Notification  received
Oct  9 14:47:53 pe1.core7914: Oct  9 13:47:52.361 GMT:  %BGP_SESSION-5-ADJCHANGE: neighbor 100.80.64.152 IPv4 Unicast vpn vrf  nyccspare1-12 topology base removed from session  BGP Notification  received
Oct  9 14:47:58 as1.core 93: Oct  9 13:47:57.631 GMT:  %PLATFORM_ENV-1-FRU_PS_SIGNAL_FAULTY: POWER_GOOD signal on power supply 1  is faulty

```


The CE switches are now logging to an new file but ommiting the ipaddress/hostname for some reason.

```

Oct  9 13:43:58 alert  : 1/1/1025: alarm_mgr: 01: 1:05 Minor DSL Down DSL line
Oct  9 13:44:22 alert  : 1/2/1025: alarm_mgr: 01: 2:09 Minor DSL Up DSL line
Oct  9 13:44:27 notice : 1/a/12  : shelfctrl: Alarm status cleared.

```

I  have tried without the filter and it remains the same. Before with  sysklogd it reported the hostname of these devices which is also  manually entered in the local host file.
A TCPdump shows the hostname, so rsyslog myst be stripping the hostname somehow:

```

10:59:12.241002 IP ce1.neti.2767 > syslog.core: SYSLOG local4.alert, length: 85
E..q....>...dA..d@.
....].^<161>OCT 10 09:59:05: alert  : 1/1/1025: alarm_mgr: 01: 1:05 Minor DSL Down DSL line

```

Syslog output:

```

Oct 10 09:59:12 alert  : 1/1/1025: alarm_mgr: 01: 1:05 Minor DSL Down DSL line

```

---

