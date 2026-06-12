---
title: "View running and stopped services in terminal?"
date: 2015-07-12
forum: General Help
---

### Post by peter1897 on 2015-07-12
Is this a accurate way to see which services are running and which are stopped:

**initctl list | grep start**

and

**initctl list | grep stop**

---

### Post by TheFu on 2015-07-12
Never heard of that command.  Daemons can be run by any user and do not need to be part of the system. Any userid can start a service that listens on any port higher than 1024 too. Keep that in mind too.

I've seen **service --status-all** as a recommended solution for this, but it will have the same limitation.

---

### Post by peter1897 on 2015-07-13
**service --status-all** command doesn't seem to be very accurate. It lists services that are running and that are stopped but without showing which services are stopped and which are running. I have to run additional commands to see the service status:

```
max@ubuntu:~$ service --status-all
 [ ? ]  acct
 [ + ]  apache2
 [ - ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  aumix
 [ ? ]  binfmt-support
 [ - ]  bootlogd
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  dbus
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ ? ]  failsafe-x
 [ - ]  grub-common
 [ ? ]  hostname
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  irqbalance
 [ ? ]  killprocs
 [ ? ]  module-init-tools
 [ ? ]  mysql
 [ ? ]  network-interface
 [ ? ]  network-interface-security
 [ ? ]  networking
 [ ? ]  ondemand
 [ ? ]  plymouth
 [ ? ]  plymouth-log
 [ ? ]  plymouth-splash
 [ ? ]  plymouth-stop
 [ ? ]  pppd-dns
 [ ? ]  procps
 [ ? ]  rc.local
 [ - ]  rsync
 [ ? ]  rsyslog
 [ ? ]  screen-cleanup
 [ ? ]  sendsigs
 [ + ]  ssh
 [ ? ]  stop-bootlogd
 [ ? ]  stop-bootlogd-single
 [ - ]  sysstat
 [ ? ]  udev
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  ufw
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ ? ]  unattended-upgrades
 [ - ]  urandom
 [ ? ]  vboxadd
 [ ? ]  vboxadd-service
 [ ? ]  vboxadd-x11
 [ ? ]  webmin
 [ ? ]  wpa-ifupdown
 [ - ]  x11-common
 [ + ]  x2goserver
```


```
max@ubuntu:~$ service ufw status
ufw stop/waiting
```

---

### Post by TheFu on 2015-07-13
Because a daemon can be started by any body, there will never be any 100% accurate list.  Perhaps systemd will solve this issue (which I doubt).  You can always write a script that checks the process table and filters only root processes - probably want to filter it on highly specific names too.  Looking in /var/run/ I see about 16 PID files, but not all daemons create PID files and they aren't all dumped into /var/run.

The greatest feature for Unix systems is the flexibility.  That makes getting a central list like this very hard.

---

