---
title: "Wanadoo wireless setup"
date: 2005-08-16
forum: General Help
---

### Post by ChrisDerson on 2005-08-16
I have a Toshiba Tecra 8200.  My work cable network connection works without problem (eth0).  I recently installed Wanadoo wireless and talk at home.  This works under Win 98 (on the laptop) and ME (on a desktop) with the USB wireless network adapter supplied.
However, when I try and use the Tecra's built in wireless connection (eth1) I get problems.  I have entered the network name and WEP key, and this seems to be working because I get signal (no signal if WEP key or ESSID removed/changed).
When I try and reach the Router (192.168.1.1) I get a 'network unreachable' error.  I've checked the firewall (with "sudo iptables -L") and no rules/filters seem to be set up, which fite with eth0 working 'out of the box'.
I've setup eth1 to use DHCP (as per working win 98 / ME setup), and have confirmed the router address as 192.168.1.1 from these boxes too.
The Windows setup instructions advise pressing a button on the wireless router before trying to connect new devices, which I have also tried, without success.
I found some notes for Mac users that suggest the setup I have should work (forgotten the address, sorry), but I was wondering if any Ubuntu users have had more success than I have.
Thanks.

---

