---
title: "Strange Firestarter activity, Back orifice 2k etc?"
date: 2005-10-17
forum: General Help
---

### Post by cowlip on 2005-10-17
I have installed Firestarter and have very strange event logs.

Time:Oct 16 14:37:26 Direction: Unknown In: Out:eth0 Port:20000 Source:192.168.2.19 Destination:c-c6a670d5.022-240-73746f23.cust.bredbandsbolaget.se Length:87 TOS:0x00 Protocol:UDP

Time:Oct 16 14:31:51 Direction: Unknown In: Out:eth0 Port:6000 Source:192.168.2.19 Destination:88.106.54.221 Length:44 TOS:0x00 Protocol:TCP Service:Xwindows  

Time:Oct 17 00:45:30 Direction: Unknown In: Out:eth0 Port:54321 Source:192.168.2.19 Destination:83.78.121.3 Length:85 TOS:0x00 Protocol:UDP Service:Back orifice 2K

IT looks like they're COMING from my computer, so what does that mean?

---

### Post by trigg on 2005-10-17
[QUOTE=cowlip]I have installed Firestarter and have very strange event logs.

Time:Oct 16 14:37:26 Direction: Unknown In: Out:eth0 Port:20000 Source:192.168.2.19 Destination:c-c6a670d5.022-240-73746f23.cust.bredbandsbolaget.se Length:87 TOS:0x00 Protocol:UDP

Time:Oct 16 14:31:51 Direction: Unknown In: Out:eth0 Port:6000 Source:192.168.2.19 Destination:88.106.54.221 Length:44 TOS:0x00 Protocol:TCP Service:Xwindows  

Time:Oct 17 00:45:30 Direction: Unknown In: Out:eth0 Port:54321 Source:192.168.2.19 Destination:83.78.121.3 Length:85 TOS:0x00 Protocol:UDP Service:Back orifice 2K

IT looks like they're COMING from my computer, so what does that mean?[/QUOTE]

Firestarter has a list of ports that correspond with known uses - so if it sees activity on that port it displays that *possible* use. Most likely it is just some website that you went to with javascript in an advertisement that is sending back usage information, or whatever it is that website advertisers want to know - but it is not a bad idea to check for rootkits with chkrootkit or rkhunter.

---

### Post by cowlip on 2005-10-17
THanks for your reply :)

LOl I have a router with NAT, so I've always avoided firewalls like thisfor that reason.   I've been up all night worrying about source of infection, do I have to format, and more ;)  


Should I use a livecd with these tools, or just right on my current computer?  The tests have come back fine so far

---

### Post by trigg on 2005-10-20
Sorry about the delayed reply - It is always "safer" to use a trusted source to run the tests. . . e.g. - a live-cd with the most recent versions of the security software you want to use.  That way you can be assured (relatively) that you are not using a compromised version of rkhunter or chkrootkit.

---

