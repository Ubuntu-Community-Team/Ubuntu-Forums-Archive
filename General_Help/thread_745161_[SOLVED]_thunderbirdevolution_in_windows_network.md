---
title: "[SOLVED] thunderbird/evolution in windows network"
date: 2008-04-04
forum: General Help
---

### Post by Milan SPK on 2008-04-04
hey guys, i installed ubuntu (as a second os, next to xp that was already there) on computer in my office, but i cant use it to send/receive email via windows mail server used in my office.
on other (windows) boxes, in thunderbird, as mail server (where i usualy put "pop3.gmail.com")  they  just put the name of the server computer ("tuhana") but when i do the same in ubuntu, it doesnt work.
i guess i need to connect to the network for thunderbird to know what "tihuana" means but i need help doing that...
i am able to surf internet and connect to other computers in the network via samba.

thanks a lot!
m

---

### Post by dcstar on 2008-04-05
> **Milan SPK said:**
> hey guys, i installed ubuntu (as a second os, next to xp that was already there) on computer in my office, but i cant use it to send/receive email via windows mail server used in my office.
on other (windows) boxes, in thunderbird, as mail server (where i usualy put "pop3.gmail.com")  they  just put the name of the server computer ("tuhana") but when i do the same in ubuntu, it doesnt work.
i guess i need to connect to the network for thunderbird to know what "tihuana" means but i need help doing that...
i am able to surf internet and connect to other computers in the network via samba.

thanks a lot!
m

Just put the name of the server in your hosts file along with it's IP address (system-Administration-Network-Hosts) - or set your DNS to use your network's internal DNS server.

---

### Post by Milan SPK on 2008-04-07
that worked! thanks so much... i am w$ free again :)

---

