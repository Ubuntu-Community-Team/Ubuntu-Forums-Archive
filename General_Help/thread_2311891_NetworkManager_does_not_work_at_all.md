---
title: "NetworkManager does not work at all"
date: 2016-01-30
forum: General Help
---

### Post by JulianLx on 2016-01-30
Hi,

NetworkManager stoped to work today when booted my Kubuntu. Config files seems OK

/var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

/etc/NetworkManager/NetworkManager.conf

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

/etc/network/interfaces

auto lo
iface lo inet loopback

nmcli shows it is not running

sudo service network-manager status
network-manager stop/waiting

Restart does not help. Tried purging and installing without success.
I am connecting trough dhclient, but many Plasma apss, includinh Kmail accounts, do no connect. Totally lost...

Julian

---

### Post by JulianLx on 2016-01-30
SOLVED
[http://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet](http://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet)

---

### Post by matt_symes on 2016-01-30
Hi

This is the third time I've come across this today. Twice on the forums and once on IRC.

Have you had an update to network-manager recently ? I'm beginning to wonder if there's a problem with network manager.

Open up a terminal and type

```
tail -n0 -f /var/log/syslog
```

Open a second terminal and type

```
sudo service network-manager start
```

Post the output that appears in the first terminal windows into your next post.

Kind regards

---

### Post by matt_symes on 2016-01-30
Hi

> **JulianLx said:**
> SOLVED
[http://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet](http://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet)

Good man ! Thanks for posting this.

Looks like there is a problem.

Kind regards

---

