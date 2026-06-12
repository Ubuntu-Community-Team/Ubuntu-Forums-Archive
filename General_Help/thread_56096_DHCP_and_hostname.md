---
title: "DHCP and hostname"
date: 2005-08-11
forum: General Help
---

### Post by Swad on 2005-08-11
We run a Windows 2000 based network at our office.  DHCP is controlled by one of our Windows 2000 servers.  I have never had luck with any of my Ubuntu workstations fully working with DHCP.  They never pass the hostname to the DHCP server and thus only get an IP lease.  If I go to the DHCP snap-in, the Ubuntu machines have no hostname next to their IP that they leased.  The problem is that other machines on the network can't see these machines except by their IP.  I can't ping a hostname or access the machine via a hostname as it never passed that info on the the DHCP server.  What is going on with this?  What can I do besides setup a static IP and a static DNS record on our DNS server?  This is an option that works, but it doesn't address why the DHCP client won't pass a hostname to the DHCP server.  This has happened two times on default installs.

---

### Post by mo_x on 2005-08-11
In the file /etc/dhcp3/dhclient.conf I have the line:
send host-name "xxxxxxxxx";
The Ubuntu installer first tried to get a network connection without a dhcp hostname. When that failed it asked for a hostname and tried again. I quess you get a connection without the hostname and this is what happend on install.

---

### Post by Swad on 2005-08-11
Yeah, I happened to run across that option while browsing the forum and tried it out.  Bingo--DHCP started showing the hostname next to the IP for the machine.  New problem?  DNS isn't picking this up for some reason like it does the rest of the computers on the network running DHCP (WIndows 2000 / XP machines).  Not sure what the deal is here, but I would assume this is outside of the scope of what Ubuntu can do.

Oh well, I just decided to go with a static IP and DNS entry as I'm wasting a lot of time on this issue at this point.

---

