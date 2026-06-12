---
title: "Small Office Server"
date: 2006-07-12
forum: General Help
---

### Post by drunkahol on 2006-07-12
I've been requested to build a small office server for a mate of mine.  He's getting an inspection from his professional body later this month and must demonstrate off-site backups.

He's got 2 laptops and a desktop in his current setup, but has only ever done 2 backups (both of which were actually done by me when I visited!).

He's got an unused Dell Dimension L800r with 128Mb RAM and 20Gb HD.  I figure 20Gb is more than enough for an OS installation, so I'm looking to increase the memory to 512Mb and stick a SATA Raid card in so I can provide a large amount of Samba shared disk.  I'll also use this space to do disk to disk backups before writing to tape.

Does anyone have any good reports on PCI SATA Raid cards with support for Linux.  I'd like online rebuilds (and hot-swap if possible) under Linux.  My other consideration is to use LVM to provide the mirroring, but I'm slightly averse to wasting CPU cycles on Raid.  I'd rather use the machine for other things like firewall, mail server, print server, spam filter, DHCP, fax server, VPN etc.

Thanks

Duncan

---

