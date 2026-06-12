---
title: "Cannot run cups on Acer C720"
date: 2014-01-13
forum: General Help
---

### Post by dyndase on 2014-01-13
I install cups on my xfce (on Acer C720 via Crouton), but I cannot run cups.
I tried restarting the service, but it said;

```

sudo /etc/init.d/cups start

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cups start
initctl: Unknown job: cups

sudo service cups restart

stop: Unknown job: cups
start: Unknown job: cups

service --status-all
 [ ? ]  alsa-restore
 [ ? ]  alsa-store
 [ ? ]  anacron
 [ ? ]  apport
 [ ? ]  avahi-daemon
 [ - ]  bootlogd
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  cups
 [ ? ]  dbus
 [ ? ]  dmesg
 [ ? ]  hostname
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  killprocs
 [ - ]  lm-sensors
 [ ? ]  module-init-tools
 [ ? ]  network-interface
 [ ? ]  network-interface-container
 [ ? ]  network-interface-security
 [ ? ]  networking
 [ ? ]  ondemand
 [ ? ]  passwd
 [ ? ]  plymouth
 [ ? ]  plymouth-log
 [ ? ]  plymouth-ready
 [ ? ]  plymouth-splash
 [ ? ]  plymouth-stop
 [ ? ]  plymouth-upstart-bridge
 [ ? ]  procps
 [ ? ]  rc.local
 [ ? ]  resolvconf
 [ ? ]  rsyslog
 [ + ]  saned
 [ ? ]  sendsigs
 [ ? ]  setvtrgb
 [ - ]  stop-bootlogd
 [ - ]  stop-bootlogd-single
 [ ? ]  sudo
 [ ? ]  udev
 [ ? ]  udev-fallback-graphics
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ - ]  unattended-upgrades
 [ - ]  urandom
 [ - ]  x11-common



```



There is a cups.conf in etc/init/ directory. Then, I don't know what to do.
Please help me... XP

---

### Post by ian-weisser on 2014-01-16
> **dyndase said:**
> 
sudo service cups restart

stop: Unknown job: cups
start: Unknown job: cups



Here's what happens when I try it on 13.10:
```
$ sudo service cups restart

cups stop/waiting
cups start/running, process 2226

```

Perhaps you need to reinstall cups.
What version of Ubuntu are you running?

---

### Post by calinb on 2015-01-02
Try this:
[https://github.com/dnschneid/crouton/wiki/Printing](https://github.com/dnschneid/crouton/wiki/Printing)

I think I made progress with the above procedure, but I have run out of time to work on it for today. I have not yet attempted to install cups_browed on my 12.04 "Precise" crouton but just typed-in the URL for my netwoked printer.  The printer now appears and is reported as "Connected" / "Idle" but the test page fails to print.

Please let me know of your results and good luck! BTW, I've been printing just fine with 12.04 over the last two years with ChrUbuntu, but the last system update renedered Ubuntu unbootable so I thought I'd try crouton.

---

### Post by calinb on 2015-01-03
I had time to confirm with my Acer Chromebook C710 (says "MODEL NO. Q1VZC" on the bottom) that the above procedure works with crouton and 12.04 LTS. I'm now printing to a D-Link "Pocket" printserver and Samsung ML-2510 using lpd//172.0.16.41. Try that on a standard Chrombook! (The local/network printer support is non-existent--who can live with that?)

Here's the link again: [https://github.com/dnschneid/crouton/wiki/Printing](https://github.com/dnschneid/crouton/wiki/Printing)

dnssd:// doesn't work in the Ubuntu printer configuration setup--probably due to some failure to access my local dns server (dns client must not be installed or something), but I'm not worred about it, because a static local IP works fine for me and I don't really need a dns client on this computer to access all the stuff stuff on my local home network.

---

