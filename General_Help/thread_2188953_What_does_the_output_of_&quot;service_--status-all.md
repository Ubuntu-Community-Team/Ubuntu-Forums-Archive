---
title: "What does the output of &quot;service --status-all&quot; mean?"
date: 2013-11-20
forum: General Help
---

### Post by vasa1 on 2013-11-20
When I run ```
service --status-all
```I get```
[11:43 AM] ~ $ service --status-all
 [ + ]  anacron
 [ - ]  apparmor
 [ ? ]  apport
 [ + ]  avahi-daemon
 [ - ]  bluetooth
 [ + ]  console-font
 [ + ]  console-setup
 [ + ]  cron
 [ - ]  cups
 [ - ]  dbus
 [ ? ]  dns-clean
 [ + ]  friendly-recovery
 [ - ]  grub-common
 [ ? ]  irqbalance
 [ ? ]  killprocs
 [ + ]  kmod
 [ ? ]  lightdm
 [ ? ]  networking
 [ + ]  ntp
 [ ? ]  ondemand
 [ ? ]  pppd-dns
 [ - ]  procps
 [ ? ]  rc.local
 [ + ]  resolvconf
 [ + ]  rfkill-restore
 [ + ]  rfkill-store
 [ - ]  rsync
 [ + ]  rsyslog
 [ ? ]  sendsigs
 [ + ]  setvtrgb
 [ - ]  sudo
 [ - ]  udev
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ - ]  unattended-upgrades
 [ - ]  urandom
 [ - ]  x11-common
 [ + ]  zram-config

```What does the output mean? I find [ ? ], in particular, quite puzzling. **man service** isn't helpful, at least to me.

---

### Post by heir4c on 2013-11-20
This link will help:
[http://superuser.com/questions/367863/how-do-interpret-the-output-of-service-status-all](http://superuser.com/questions/367863/how-do-interpret-the-output-of-service-status-all)

---

### Post by bab1 on 2013-11-20
> What does the output mean? I find [ ? ], in particular, quite puzzling. man service isn't helpful, at least to me. 

The Upstart Service script that runs and then supplies the output lists *all* packages installed.  Since service is an Upstart tool it only looks at Upstart initiated processes.  The processes that are not Upstart initiated are marked with a "?".

For example you have these installed but they don't use Upstart to launch so there status is unknown```

 [ ? ]  dns-clean
 [ ? ]  irqbalance
 [ ? ]  killprocs
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot

```

---

### Post by vasa1 on 2013-11-20
Thanks to both of you :) Marking this [Solved].

---

### Post by steeldriver on 2013-11-20
fyi, for the services that are managed via init rather than upstart, you can use initctl

```
initctl list
```

---

