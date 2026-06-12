---
title: "syslog in different files."
date: 2015-03-16
forum: General Help
---

### Post by lucas36 on 2015-03-16
Hi guys

In this moment im working with several remote routers in the company.
The law states we have to keep a log of the network activity for each device. So I have installed a syslog server (rsyslog).

I know that I have to configure each router of the network to point the syslog server.

However, I dont know what I have to do to save the log information in individual files, e.g,

router_1 send info to log_file_1
router_2 send info to log_file_2
router_3 send info to log_file_3

so, in this way, we avoid to have a big file with information of all devices into a unique file.

The point is that each device only can be configured with the remote address, and no more options.

Can someone explain/help me with this configuration, to save the information in individual files?

Thank you very much

---

### Post by lucas36 on 2015-03-17
Hi guys ...some suggestion?

---

### Post by Lars Noodén on 2015-03-17
Edit: oops

---

### Post by Lars Noodén on 2015-03-17
Have you read through the manual page for [rsyslog.conf](http://manpages.ubuntu.com/manpages/trusty/en/man5/rsyslog.conf.5.html) to get an idea of what it shows and then looked at the existing configurations in /etc/rsyslog.conf and /etc/rsyslog.d/* to get an idea of how they are actually deployed?  You'll probably what to eventually add your own file to /etc/rsyslog.d/

---

### Post by SeijiSensei on 2015-03-17
Since the composite log will include the names of the routers in the entries, I'd just split the log with grep:
```
grep router1 /var/log/syslog > /var/log/router1.log
```
If you put this in a script that runs overnight from cron and creates dated logs, you'll build up a nice archive.
```

#!/bin/sh

LOG=/var/log/syslog
ROUTERS="router1 router2 router3" 
TODAY=$(date +%Y%m%d)

for r in $ROUTERS
do
    grep $r $LOG > /var/log/$r-$TODAY.log
done

exit 0

```
If you use logrotate, I'd set the frequency for syslog to daily, then have this script run before logrotate is executed.

---

### Post by Lars Noodén on 2015-03-17
> **SeijiSensei said:**
> I'd just split the log with grep

rsyslog can sort the log records into separate files as it comes in.  That would be fewer moving parts.

---

### Post by SeijiSensei on 2015-03-17
Ah, I didn't know that.  I've only used remote logging in a couple of situations and typically not with multiple reporting devices.

---

### Post by btindie on 2015-03-17
You can use rsyslog to write to multiple files. In /etc/rsyslog.d create a config file for your routers.

```

:fromhost-ip, isequal, "1.2.3.4"   /var/log/%HOSTNAME%.log
& ~
:fromhost-ip, isequal, "1.2.3.5"   /var/log/%HOSTNAME%.log
& ~
:fromhost-ip, isequal, "1.2.3.6"   /var/log/%HOSTNAME%.log
& ~

```

The "& ~" bit tells rsyslog to then drop the message so it doesn't appear in any of the other logs.

---

### Post by Habitual on 2015-03-17
> **btindie said:**
> You can use rsyslog to write to multiple files. In /etc/rsyslog.d create a config file for your routers.

```

:fromhost-ip, isequal, "1.2.3.4"   /var/log/%HOSTNAME%.log
& ~
:fromhost-ip, isequal, "1.2.3.5"   /var/log/%HOSTNAME%.log
& ~
:fromhost-ip, isequal, "1.2.3.6"   /var/log/%HOSTNAME%.log
& ~

```

The "& ~" bit tells rsyslog to then drop the message so it doesn't appear in any of the other logs.

Good stuff.
I use this on the receiver's /etc/rsyslog.conf
```
$template RemoteHost, "/mnt/kibana/remotes/%HOSTNAME%/%HOSTNAME%.log"
*.* -?RemoteHost

$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat

## Rulesets
# Local Logging
$RuleSet local
kern.*                                                  /var/log/messages
*.info;mail.none;authpriv.none;cron.none                /var/log/messages
authpriv.*                                              /var/log/secure
mail.*                                                  -/var/log/maillog
cron.*                                                  /var/log/cron
*.emerg                                                 :omusrmsg:*
uucp,news.crit                                          /var/log/spooler
local7.*                                                /var/log/boot.log
$DefaultRuleset local

# Remote Logging
$RuleSet remote
*.info;mail.none;authpriv.none;cron.none                ?RemoteHost
```

One of several ways, I'm sure.

---

