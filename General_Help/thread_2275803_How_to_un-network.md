---
title: "How to un-network"
date: 2015-04-28
forum: General Help
---

### Post by bilkay on 2015-04-28
Ubuntu 12.04 - I have this PC that I took off the network and it is now just serving a scanner and printer. I only turn it on when I want to scan something, and it takes a LONG time waiting for a network configuration it's never going to get. I tried renaming the file /etc/rc6.d/S35networking to XS35networking, but it didn't seem to make a difference. I also tried Administration->Network Tools, but I didn't see anything that would help. I'd like to know if there's a simple, reversible (in case I want to put it back on the network) way to make it stop trying to start up the network.

---

### Post by grahammechanical on 2015-04-28
It is years since I used 12.04 but how about clicking the Network Manager Icon in the top panel and selecting Edit Connections? Then edit each connection (I assume you mean WiFi?) in the General tab and untick the box labelled Automatically Connect to this network when it is available. There is nothing stopping you from deleting the connection completely. That certainly would do it. But then you would have to set up the connection again.

---

### Post by bilkay on 2015-04-28
It never had wi-fi, it only had a wired connection to the router. I tried had tried your suggestion and there's no way to delete it or disable it. Thanks for responding.

---

### Post by steeldriver on 2015-04-28
[LIST]
[*]if you have interface(s) (other than the loopback interface 'lo') defined in the /etc/network/interfaces file, delete them, or comment them out 
[*]either remove (using Software Center, or apt-get) the network-manager package, or prevent it from being started at boot time by creating a network-manager.override file in /etc/init containing the single word 'manual' e.g. 
[/LIST]
[INDENT]```

echo 'manual' | sudo tee /etc/init/network-manager.override

```
[/INDENT]

---

### Post by bilkay on 2015-04-29
> **steeldriver said:**
> 
[LIST]
[*]if you have interface(s) (other than the loopback interface 'lo') defined in the /etc/network/interfaces file, delete them, or comment them out 
[*]either remove (using Software Center, or apt-get) the network-manager package, or prevent it from being started at boot time by creating a network-manager.override file in /etc/init containing the single word 'manual' e.g. 
[/LIST]
[INDENT]```

echo 'manual' | sudo tee /etc/init/network-manager.override

```
[/INDENT]


Bingo!

Thanks Much!

---

