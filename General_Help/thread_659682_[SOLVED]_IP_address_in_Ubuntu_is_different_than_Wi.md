---
title: "[SOLVED] IP address in Ubuntu is different than Windows"
date: 2008-01-06
forum: General Help
---

### Post by FuturePilot on 2008-01-06
I just realized that there seems to be a discrepancy between my IP address in Ubuntu and Windows. Ubuntu reports one IP address but when I boot into Windows it's a different address. But if I boot back into Ubuntu it's the same one from before. So Ubuntu thinks I have one IP address and Windows thinks I have a different one. How can this be? An IP address should not be OS specific. :confused:

---

### Post by scrooge_74 on 2008-01-06
probably your router or ISP is giving you different address after each reboot, unless you are just looking at an internal address or the address of a diferent network card

---

### Post by FuturePilot on 2008-01-06
No I don't think it's always different. In Ubuntu I have IP address A. I boot into Windows and have IP address B. I boot back into Ubuntu and I have IP address A again.:-k

---

### Post by PeterJS on 2008-01-06
Might have to do with DHCP lease times. Windows leases address A for a month, reboot to ubuntu it requests an address but doesn't have the ticket from the windows lease, so the dhcp server being none to smart doesn't bother to check the MAC addresses and leases address B for a month. Boot back to windows and it resumes it's month long lease of address A.

---

### Post by FuturePilot on 2008-01-06
> **PeterJS said:**
> Might have to do with DHCP lease times. Windows leases address A for a month, reboot to ubuntu it requests an address but doesn't have the ticket from the windows lease, so the dhcp server being none to smart doesn't bother to check the MAC addresses and leases address B for a month. Boot back to windows and it resumes it's month long lease of address A.

Interesting. Never knew that. That might just be. I'll have to wait and see what happens. 
Makes a lot of sense though :)

---

### Post by PeterJS on 2008-01-06
Bare in mind that I just pulled the one month figure out of thin air, I have no idea what kind of lease times your ISP uses.

---

### Post by rkillcrazy on 2008-01-06
Yes, for as long as the client and the DHCP server are on the same network, the DHCP server will attempt to give the client the same IP over and over again.  This generally happens until a lease expires on PC-1 and a new client (PC-2) comes along and grabs the IP before PC-1 has the chance to renew his lease.  Generally speaking, PC-1 will have the same IP given to it 'cause it's always on when its lease expires and can therefore renew it immediately.  However, if PC-1 is off when its lease expires and PC-2 comes online, looking for a DHCP address, the DHCP server will give that lease to the next in line - which would be PC-2 in this case.  In most consumer routers (Netgear and Linksys routers bought from your local electronic super store) the leases are 24 hours or several days.  This can be changed, depending on the network's needs.

01-06-08
0047 EST

---

### Post by FuturePilot on 2008-01-06
Yep that seems to be it.  I hooked up my laptop and had IP address C. It does make sense. If I were a DHCP server ( :lolflag: ) and I was dealing with a dual boot machine, I wouldn't see 1 computer but 2 and would treat it as such. Thanks for the help everyone. ;)

---

