---
title: "configuring bittornado"
date: 2005-10-03
forum: General Help
---

### Post by Josef K. on 2005-10-03
I'm trying to download a couple of torrent file with bittornado, but I've never seen "green status" (actually I've never seen a byte! ](*,) )
I've also followed instruction of [www.portforward.com](www.portforward.com) (I'd hope so, since there're windows only :( ) but nothing changed
Am I missing some setting? :confused:

---

### Post by Dennis Laumen on 2005-10-03
Could you give us some more information like are you using a router, what ports have you forwarded already, are you using a firewall?

---

### Post by Josef K. on 2005-10-03
I'm using a zyxel650HE (router+firewall)
according to portforward.com I've enabled in NAT portforwarding of 10000-10004 to IPaddress 192.168.1.1
I didn't make any change to default-ubuntu iptables (should I?) nor in zyxel firewall (since it used to work under winxp)

---

### Post by Dennis Laumen on 2005-10-03
BitTorrent uses the ports 6881-6889 by default. Try changing the forwarded ports and see if it helps.

---

### Post by Josef K. on 2005-10-04
TKS
I've removed forwarding 1000\10004 and put 6881-6889: seems not worked :(

---

### Post by Dennis Laumen on 2005-10-04
Do you have a firewall installed locally (for example Firestarter?).

---

### Post by Josef K. on 2005-10-04
no 
I just left (ubuntu) default setting in iptable

---

### Post by Dennis Laumen on 2005-10-05
Weird, it should really work then. How is BitTornado configured? Does it use any other ports?

You forwarded the _TCP_ ports didn't you, only forwarding the UDP ports won't work. 

Does Gnome BitTorrent get any green lights? If so, this will probably be a bug in BitTornado (unless you reconfigured the BitTornado ports).

Does your router specifically block any other ports? Port 6969 is being used by trackers, if this port is unreachable it won't work either (It is not needed to forward this port, it just needs to be reachable).

---

### Post by Josef K. on 2005-10-06
bittornado uses ports 10000 to 10004, and I've forwarded both TCP/UDP

gnome-bittorrent doesn't work either, but the funny thing is that azureus seems to work (actually I got the green light but don't download a bit :confused: )

maybe is a torrent-file fault (and I'm trying to download torrents not seeded anymore) since azureus plugin (that azureus seems to download using a torrent) were downloaded without any problem

I'll try to find other files then I'll report :)

---

### Post by Dennis Laumen on 2005-10-06
Hmm it probably is a torrent problem then :D

Just try downloading an Ubuntu ISO. Those torrents are always filled with people! If it downloads that, nothing is wrong with your settings!

---

### Post by sad780 on 2005-10-09
For this linux newbie, Bittornado does absolutely nothing. It stays red, doesn't connect to anyone, and doesn't download anything. 

Gnome bittorrent works fine for some torrents, but gives me an 'invalid client port' error for some others. It is also very slow. 

I am using an actiontec dsl modem/router and my service is through Qwest. As far as I know I have no firewall. I have not changed any router or network settings. Everything always worked fine in Windows.

Any suggestions or help would be appreciated.

---

### Post by Dennis Laumen on 2005-10-10
Hi sad780!

You need to forward some ports in your router anyway. Ports 6881-6889 TCP. You can do it in your router's web interface.

---

### Post by pokerface on 2006-03-30
does anyone know how to configure bittornado threw command line? because i have it installed but dont have it even working in ubuntu (which isnt a problem for because i plan on only using the command line for bittornado). i want to change the ports!! but i have no idea on how to do so!

---

