---
title: "Orinoco PCMCIA 8470-WD Issues"
date: 2005-10-24
forum: General Help
---

### Post by DarthGroznii on 2005-10-24
My present setup is an HP Compaq nx7000 laptop, running Breezy - as the native Centrino chipset only communicates at the 802.11b standard, I've tried to install a Proxim Orinoco PCMCIA 8470-WD card in the PCMCIA slot.

Attempts to activate it using Networking in the GUI have failed - the driver detects it properly, it is set at ath0. 

I've also done a lspci -v and this is the reading for the card - 

0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: PROXIM Inc: Unknown device 0a40
        Flags: bus master, medium devsel, latency 168, IRQ 5
        Memory at 50800000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2


I tried to rule out a conflict with the Centrino networking by blacklisting the ipw2100 driver in /etc/hotplug/blacklist.  Still no joy - the card simply will not engage and the green lights for power and networking flash back and forth.  

Please advise on what I'm doing wrong in getting this card activated.

---

### Post by DarthGroznii on 2005-10-25
A suggestion or even a clue would be appreciated - this is the second card from the suggested hardware list I've tried to install and had no success.

---

### Post by DarthGroznii on 2005-10-27
Further information - tried the following commands:

> 
iwconfig ath0 essid "any"
ifconfig eth1 down
ifconfig ath0 up
dhclient ath0


Returns were as follows:

> 
sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/ath0/00:20:a6:57:a6:aa
Sending on   LPF/ath0/00:20:a6:57:a6:aa
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67
interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67
interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67
interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67
interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67
interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67
interval 18
DHCPDISCOVER on ath0 to 255.255.255.255 port 67
interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Please advise.  The native Centrino wireless networking works just fine.

---

### Post by DarthGroznii on 2005-10-27
Any ideas on this?

---

