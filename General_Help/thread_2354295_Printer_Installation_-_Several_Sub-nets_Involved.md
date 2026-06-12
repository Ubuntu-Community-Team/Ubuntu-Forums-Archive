---
title: "Printer Installation - Several Sub-nets Involved"
date: 2017-03-01
forum: General Help
---

### Post by shadragon on 2017-03-01
Morning, 

I have a 14.04 Kubuntu LAMP server and I'm trying to get a printer hooked up to it. 

The HP LaserJet P3015 Printer in question is on a dedicated sub-net for  support devices like NAS, printers, etc. (192.168.17.0/24) 

The Printer is shared off of a Windows 2012 server that is on the Corp  network (192.168.18.0/24). 2012 Server has multiple NIC's and is on both  Corp/Guest networks and has access to the Printer 17.0 sub-net.

The LAMP server is a VM on our Guest network (192.168.0.0/23). By policy, it has no path to get to the 17.0 sub-net.

The LAMP server can ping the 2012 server on the Guest network, but I  can't seem to connect to the printer share. I can connect Windows  machines on Guest to that print share without issue. 

Any tips?

---

### Post by SeijiSensei on 2017-03-01
Install the smbclient package if it's not already there.  Then try
```
smbclient -L name_of_server [-I ip.addr.of.server]
```
You may need the add the optional -I directive (without the braces) depending on how name resolution is handled at your site.

You should get back a list of all visible shares on the server.  Is the printer among them?

---

### Post by stewartalexanderlittle on 2017-03-01
Is system-config-printer suitable for this process? Have you tried this software for printer setup.

---

### Post by ajgreeny on 2017-03-01
Threads merged.
**Please do not create duplicate posts; it is confusing for all including you and dilutes the forum's ability to help.**

Four duplicates were posted and two of those were answered; surely you can see that it is impossible for everyone to keep trying to figure out where the problem has got to if you ask the same thing in many different places.

---

