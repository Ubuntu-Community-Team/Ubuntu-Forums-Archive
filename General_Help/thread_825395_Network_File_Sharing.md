---
title: "Network File Sharing"
date: 2008-06-10
forum: General Help
---

### Post by lorenfb on 2008-06-10
Running 7.04 and 8.04 on two different machines.
Both have problems with accessing either a NAS
or WIN XP file sharing on the network when a DSL modem 
is attached to the router. When network access is attempted 
by Ubuntu, the DSL modem LAN light flickers and Ubuntu
is unable to access network files.

Once the modem is powered off and the router is reset, 
both machines can access the NAS or XP files on the network.
To again access the internet via the DSL modem, the
router must be reset after the modem is powered on which 
no longer allows access to the NAS nor the XP files
by the Ubuntu machines.

Using a Linksys router (non-wireless). Tried another
router (Netgear) and the same problem occurs. Using both
XP and MAC O/S machines on the network which have no problems
accessing the NAS nor using file sharing with the DSL modem 
attached to the router.

Thanks for your insights.

---

### Post by lorenfb on 2008-08-24
The problem was the DSL modem (Westell) which attempted to connect
to internet when a local general network address was given by
Ubuntu. Another DSL modem which was an integrated modem/router/wifi
(Verizon - GT704WGV) did not have this problem.

With further troubleshooting, the modem problem was easily resolved
by a more direct Ubuntu network addressing approach:

NAS address: 192.168.1.XXX

Then to access the share on the NAS;

smb://192.168.1.XXX/share

Thanks to all that helped to provide insights.

---

