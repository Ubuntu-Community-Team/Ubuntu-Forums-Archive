---
title: "resolv.conf always blank on reboot!"
date: 2017-11-24
forum: General Help
---

### Post by emskie on 2017-11-24
Hi guys

my resolv.conf is always blank whenever i reboot my OS and every time I have to manually enter DNS settings into the file to connect to the internet.
note this only started happening when I installed expressvpn

any suggestions on how to fix this issue ?

sorry I am very new to this OS

---

### Post by HermanAB on 2017-11-24
The machine needs to get that information via DHCP over the VPN - the VPN got to be up first.  So you should be able to recover it by jogging the Networkmanager widget.

---

### Post by SeijiSensei on 2017-11-24
If you're using static addressing with an entry in /etc/network/interfaces, you need to add a "dns-nameservers" line to the entry as described here: [https://help.ubuntu.com/lts/serverguide/network-configuration.html#name-resolution](https://help.ubuntu.com/lts/serverguide/network-configuration.html#name-resolution)

---

