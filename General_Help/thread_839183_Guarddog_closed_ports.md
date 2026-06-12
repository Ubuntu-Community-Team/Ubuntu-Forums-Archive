---
title: "Guarddog closed ports"
date: 2008-06-24
forum: General Help
---

### Post by screaminfakah on 2008-06-24
Hello,
I am using Ubuntu Studio 8.04 and have recently installed Guardog.  I enabled all of the standard protocols like dns, ftp, http, https, bittorrent peers, bittorrent tracker.
When I first installed and set it up Transmission worked fine.  I did some recommened updates for the OS yesterday and now Guarddog will not open a port for Transmission.  I tried creating a protocol for TCP and UDP for the port Transmission is trying to use but Guarddog will not open the port.
I even uninstalled and reinstalled Transmission and reset guarddog and setup protocols again with the same end result.
I am kind of confused as what to do next.

Thanks

---

### Post by rbanavara on 2008-06-24
For Azureus, the document says to use the following ([http://www.azureuswiki.com/index.php/NAT_problem):](http://www.azureuswiki.com/index.php/NAT_problem):)

         /sbin/iptables -I INPUT -p tcp --dport <your_port_number> -j ACCEPT
         /sbin/iptables -I INPUT -p udp --dport <your_port_number> -j ACCEPT

You can use the same for transmission (beleive firewall is setup using iptables in ubuntu).

---

