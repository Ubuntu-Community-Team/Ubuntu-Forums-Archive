---
title: "False &quot;/home Disk Full&quot; Message, LAN fails"
date: 2013-04-24
forum: General Help
---

### Post by abost on 2013-04-24
We're running a LAN with an Ubuntu 12.04 Server as our central machine using isc-dhcp-server. Yesterday, the LAN stopped working, and running sudo dhclient on client computers got no response from the server. DHCPREQUESTs no longer show up in /var/log/syslog on the server. Curiously, on the server (on which I installed Unity for other users), a GUI message had popped up saying something to the effect of "Your /home disk only has 1.1 GB remaining, click here to open Disk Usage Analyzer", but df -h shows that disk still has 1.3 TB free space remaining:
 
/dev/sdb        3.6T  2.2T  1.3T  64% /home


We run NFS so that the /home directory on the server gets mounted on the client computers (which are all running Ubuntu 10.04 LTS). On those computers, a similar GUI message popped up saying something like "the disk /mnt/server_home is almost full". Does anyone know if these things might be related? I can't understand why the DHCP server would suddenly stop responding. The /var/lib/dhcp/dhcpd.leases file has all of the entries for the IP addresses handed out to the client computers, but all of the hostname entries are gone.

If anyone has a theory or two I'd love to hear it. Thanks.

---

### Post by Bashing-om on 2013-04-24
abost; Hi !

What returns from terminal codes:
```

df -h
du -h --max-depth=1 | sort -hr
``` Looking for large directories/files.
see:
```

man df 
man du
```

Many times if house cleaning has not been maintained, /boot and /var/log can become quite large, filling up the partition.
(/var/log full from a system error and running amuck ??)[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by abost on 2013-04-24
Heh, turns out it was totally a network thing: someone had plugged a single ethernet cable into two ports on the same switch and that had caused some sort of loop that the switch didn't detect. Apparently the NFS message was related to the network loss. Figures.

Cheers!

---

### Post by Bashing-om on 2013-04-24
All's well that ends well !
[INDENT=3]
Happy trails to you -
[/INDENT]

---

