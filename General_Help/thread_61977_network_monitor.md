---
title: "network monitor?"
date: 2005-09-02
forum: General Help
---

### Post by earobinson on 2005-09-02
I have 8 computers on my home network 3 ubuntu and the rest windows, i want to run a network monitor tool to figure out why the network keeps droping with all the windows computers pluged in (im thinking virus) any good tools you know of (note all computers are pluged into a linux router)

---

### Post by KingBahamut on 2005-09-02
nmap - commandline port scanner
iptraf - Packet analysis
tcpdump - advance user only
ethereal - graphical expression of tcpdump 
etherape - graphical traffic analyzer 

Using these 5 you should have no problem tracking down the problem and shutting down whatever is causing you pain.

---

### Post by earobinson on 2005-09-03
[QUOTE=KingBahamut]nmap - commandline port scanner
iptraf - Packet analysis
tcpdump - advance user only
ethereal - graphical expression of tcpdump 
etherape - graphical traffic analyzer 

Using these 5 you should have no problem tracking down the problem and shutting down whatever is causing you pain.[/QUOTE]
 and you claim not to be a pro good sir..


thanks

cheers

---

### Post by [pl]ice on 2005-09-03
it't not wless is it?
 i had something, which sends heaps of arp requests, kinda spyware in xp or something. tcpdump showed it.

---

### Post by KingBahamut on 2005-09-03
You can alternately run 

Arping - Arping is an ARP level ping utility. It's good for finding out if an IP is taken before you have routing to that subnet. It can also ping MAC addresses directly. This can help specially if your like me, and base your iptables rules on the MAC , and not the IP. 

and 

ArpAlert - uses ARP address monitoring to help prevent unauthorized connections on the local network. If an illegal connection is detected, a program or script is launched, which could be used to send an alert message, for example.


For wireless stuff, if you have a wirless card in your system, PCI, USB or PCMCIA, you can use these utilities as well

Airsnort - AirSnort is a wireless LAN (WLAN) tool that recovers encryption keys. It operates by passively monitoring transmissions, computing the encryption key when enough packets have been gathered.

Airfart - AirFart is a wireless tool created to detect wireless devices, detect their signal strengths, and present them to the user in an easy-to-understand fashion. It is written in C/C++ with a GTK front end. Airfart supports all wireless network cards supported by the linux-wlan-ng Prism2 driver.

Kismet - Kismet is an 802.11 layer 2 wireless network detector, sniffer, and intrusion detection system. It will work with any wireless card which supports raw monitoring (rfmon) mode, and can sniff 802.11b, 802.11a, and 802.11g traffic. It identifies networks by passively collecting packets and detecting standard named networks, detecting (and given time, decloaking) hidden networks, and inferring the presence of nonbeaconing networks via data traffic.

Aircrack - aircrack is a set of tools for auditing wireless networks. It consists of: airodump (an 802.11 packet capture program), aireplay (an 802.11 packet injection program), aircrack (static WEP and WPA-PSK cracking), and airdecap (decrypts WEP/WPA capture files).

And no, im not a Pro. 

Im just Some guy.

---

