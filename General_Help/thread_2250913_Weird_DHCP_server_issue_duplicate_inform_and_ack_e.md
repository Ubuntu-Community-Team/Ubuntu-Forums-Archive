---
title: "Weird DHCP server issue duplicate inform and ack entries in log"
date: 2014-10-31
forum: General Help
---

### Post by barroncm on 2014-10-31
This does this for all clients. 
The dhcp server is authoritative and mac filtered.
Any Ideas as to why this is occurring?

Oct 31 17:57:50 server2 dhcpd: DHCPINFORM from 10.10.2.8 via eth0                                                                              
Oct 31 17:57:50 server2 dhcpd: DHCPINFORM from 10.10.2.8 via eth0                                                                              
Oct 31 17:57:50 server2 dhcpd: DHCPACK to 10.10.2.8 (00:15:00:1b:73:cd) via eth0                                                               
Oct 31 17:57:50 server2 dhcpd: DHCPACK to 10.10.2.8 (00:15:00:1b:73:cd) via eth0

---

### Post by barroncm on 2014-11-01
Anyone ?
Any Ideas?

---

