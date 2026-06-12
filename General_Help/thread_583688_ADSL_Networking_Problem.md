---
title: "ADSL Networking Problem"
date: 2007-10-20
forum: General Help
---

### Post by nubie777 on 2007-10-20
Recently my connection to my dsl line would: (1) not work or (2) fail every about 10 minutes after I did a network restart.  I replaced  NIC. Consequently, my network settings went from eth1 to eth2.  I edited /etc/init.d/interfaces to reflect eth2 as follows:

# The primary network interface
auto eth2
iface eth2 inet dhcp

I installed arno-iptables-firewall and configured it opening tcp ports 80, 443 (https) & 3306 (mysql).  

Please take a look at the attached png file.  It shows the output from:
1. Devices - Network Tools (from Admin Menu) for eth2, IP 192.168.1.69. 
2. Nmap Front End for IP 192.168.1.[COLOR="Red"]69[/COLOR]
3. Nmap Front End for IP 192.168.1.[COLOR="Red"]68[/COLOR] 
4. Network Settings - shows my ethernet connections, fyi.

This is what is confusing:
On Network Tools- eth2 shows IP of 192.168.1.69 which is my dsl line.  On Namp for IP ....69 port 80 is not open, but on Namp for IP ....68, port 80 is open. If I am using 192.168.1.69 to get to the internet, port 80 is closed 192.168.1.69, but it is open on 192.168.1.68.  _Can anyone explain why I have internet access when port 80 is closed on the IP I'm using for internet access._

Thanks much,
Cheers...

---

