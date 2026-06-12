---
title: "Dependency Problems with apt?"
date: 2020-11-02
forum: General Help
---

### Post by sniper8752 on 2020-11-02
I was doing a dist-upgrade, and was not able to login to the console to interact with the upgrade.  I had to restart it, and continue doing updates.  Before I could do more updates, it had me do dpkg --configure -a.  After that, I did a apt update/upgrade.  But I am getting errors on syslog.  I thought that apt would resolve dependencies?  Here is what I am seeing:

```

...
[FONT=monospace][COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package syslog-ng-mod-riemann (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of syslog-ng-mod-tag-parser:[/COLOR]
 syslog-ng-mod-tag-parser depends on syslog-ng-abi-3.13-0; however:
  Package syslog-ng-abi-3.13-0 is not installed.
  Package syslog-ng-core which provides syslog-ng-abi-3.13-0 is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package syslog-ng-mod-tag-parser (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of syslog-ng-mod-xml-parser:[/COLOR]
 syslog-ng-mod-xml-parser depends on syslog-ng-abi-3.13-0; however:
  Package syslog-ng-abi-3.13-0 is not installed.
  Package syslog-ng-core which provides syslog-ng-abi-3.13-0 is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package syslog-ng-mod-xml-parser (--configure):[/COLOR]
 dependency problems - leaving unconfigured
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] dependency problems prevent configuration of syslog-ng-mod-extra:[/COLOR]
 syslog-ng-mod-extra depends on syslog-ng-mod-json (>= 3.13.2-3); however:
  Package syslog-ng-mod-json is not configured yet.
 syslog-ng-mod-extra depends on syslog-ng-mod-json (<< 3.13.2-3.1~); however:
  Package syslog-ng-mod-json is not configured yet.

[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package syslog-ng-mod-extra (--configure):[/COLOR]
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 syslog-ng-core
 syslog-ng-mod-redis
 syslog-ng-mod-python
 syslog-ng-mod-map-value-pairs
 syslog-ng-mod-smtp
 syslog-ng-mod-geoip
 syslog-ng-mod-amqp
 syslog-ng-mod-sql
 syslog-ng-mod-json
 syslog-ng-mod-getent
 syslog-ng-mod-snmptrapd-parser
 syslog-ng-mod-stomp
 syslog-ng-mod-mongodb
 syslog-ng-mod-stardate
 syslog-ng-mod-add-contextual-data
 syslog-ng-mod-graphite
 syslog-ng-mod-riemann
 syslog-ng-mod-tag-parser
 syslog-ng-mod-xml-parser
 syslog-ng-mod-extra
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT]
```

How do I resolve these?

---

### Post by blackbird34 on 2020-11-02
Have you tried the command that resolves missing dependencies?

```
sudo apt install -f
```

And if so, does it work, or what does it spit out?

---

### Post by Bashing-om on 2020-11-02
sniper8752; Hello too -

In addition to blackbird34's request it will be instructive to know the source of the syslog-ng package.

What also returns for:
```

apt policy syslog-ng-core

```

[INDENT]if apt is not happy
[INDENT][INDENT]no one is happy
[/INDENT][/INDENT][/INDENT]

---

### Post by sniper8752 on 2020-11-03
```
[FONT=monospace][COLOR=#000000]Reading package lists... Done[/COLOR]
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

[/FONT]
```

```
[FONT=monospace][COLOR=#000000]syslog-ng-core:[/COLOR]
  Installed: 3.25.1-3
  Candidate: 3.25.1-3
  Version table:
 *** 3.25.1-3 500
        500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status

[/FONT]
```

---

