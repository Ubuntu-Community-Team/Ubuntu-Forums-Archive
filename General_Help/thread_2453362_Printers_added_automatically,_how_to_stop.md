---
title: "Printers added automatically, how to stop?"
date: 2020-11-08
forum: General Help
---

### Post by glennra12 on 2020-11-08
I have a new Ubuntu 20.04 install.  In Settings, under Printers, a duplicate entry keeps getting added for my networked Samsung laser printer.  Sometimes, if applications or users unintentionally choose to print through this extra entry, it is configured wrong and lots of paper and toner get wasted.

So far I've tried:

/etc/cups/cups-browsed.conf:  BrowseRemoteProtocols none, BrowseLocalProtocols none
sudo systemctl stop cups-browsed
sudo systemctl disable cups-browsed
sudo systemctl mask cups-browsed
Uninstalling the cups-browsed package

This all stopped printer entries being re-added continuously.  Still, unwanted printer entries keep appearing after I reboot the machine, and whenever I print something.  This leads me to believe that more than cups-browsed is involved in this behavior.  How do I stop it for good?

Thanks!
Rob

---

### Post by TheFu on 2020-11-09
Avahi running on the clients??

---

### Post by glennra12 on 2020-11-10
Appears to be:

$ sudo systemctl status avahi-daemon
&#9679; avahi-daemon.service - Avahi mDNS/DNS-SD Stack
     Loaded: loaded (/lib/systemd/system/avahi-daemon.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2020-11-08 18:00:45 MST; 1 day 7h ago
TriggeredBy: &#9679; avahi-daemon.socket
   Main PID: 1158 (avahi-daemon)
     Status: "avahi-daemon 0.7 starting up."
      Tasks: 2 (limit: 19084)
     Memory: 2.6M
     CGroup: /system.slice/avahi-daemon.service
             &#9500;&#9472;1158 avahi-daemon: running [cydonia.local]
             &#9492;&#9472;1207 avahi-daemon: chroot helper


Nov 09 18:46:22 cydonia avahi-daemon[1158]: Interface enp34s0.IPv6 no longer relevant for mDNS.
Nov 09 18:46:22 cydonia avahi-daemon[1158]: Withdrawing address record for 192.168.2.100 on enp34s0.
Nov 09 18:46:22 cydonia avahi-daemon[1158]: Leaving mDNS multicast group on interface enp34s0.IPv4 with address 192.168.2.100.
Nov 09 18:46:22 cydonia avahi-daemon[1158]: Interface enp34s0.IPv4 no longer relevant for mDNS.
Nov 09 22:17:06 cydonia avahi-daemon[1158]: Joining mDNS multicast group on interface enp34s0.IPv6 with address fe80::fbc4:fd09:5582:5a04.
Nov 09 22:17:06 cydonia avahi-daemon[1158]: New relevant interface enp34s0.IPv6 for mDNS.
Nov 09 22:17:06 cydonia avahi-daemon[1158]: Registering new address record for fe80::fbc4:fd09:5582:5a04 on enp34s0.*.
Nov 09 22:17:06 cydonia avahi-daemon[1158]: Joining mDNS multicast group on interface enp34s0.IPv4 with address 192.168.2.100.
Nov 09 22:17:06 cydonia avahi-daemon[1158]: New relevant interface enp34s0.IPv4 for mDNS.
Nov 09 22:17:06 cydonia avahi-daemon[1158]: Registering new address record for 192.168.2.100 on enp34s0.IPv4.

---

### Post by HermanAB on 2020-11-10
I wondered why avahi is one of the things I always turn off, but this seems to be another good reason.

---

