---
title: "Installing wifi card on linux router with lan card"
date: 2015-08-03
forum: General Help
---

### Post by andrew.robbins.fli on 2015-08-03
[COLOR=#000000]Hi all,[/COLOR]

[COLOR=#000000]I have a linux router that I'm running with Ubuntu server. It does DHCP,DNS,ftp, fns, etc. I have had it running only as a lan network and want to add wireless capabilities, so that I have wired a wireless network issuing IP's in the same range. i am not trying to create two separate subnets, rather I want the eth1 and wlan0 interfaces to be linked. I tried to setup the network using the routers page on wired and wireless([/COLOR][https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)[COLOR=#000000]), but the config file when applied does nothing, but bring down my eth1 interface.[/COLOR]

[COLOR=#000000]Here is the interface configuration that I want:[/COLOR]
[COLOR=#000000]eth0 is dhcp assignment and is my wan interface[/COLOR]
[COLOR=#000000]eth1 and wlan0 are static and are the interfaces that the server services outputted on.[/COLOR]

[COLOR=#000000]Note: I'm running Ubuntu Server 14.04LTS with a webmin GUI interface[/COLOR]

[COLOR=#000000]Any ideas how the interfaces file should be ammended?[/COLOR]

[COLOR=#000000]-Andrew[/COLOR]

---

