---
title: "Load firewall rules at start up"
date: 2007-07-07
forum: General Help
---

### Post by bowens44 on 2007-07-07
I have firewall rules that I have written. They work as they should. I can load them by doing sudo iptables-restore < /etc/firewall-riles. I haven't been able to figure out how to load these at boot up. I'm really not interested in using firestarter or scripts that create the rules.

What is the best way to load these at boot?

Thanks!

---

### Post by bowens44 on 2007-07-07
Never mind. I found what I was looking for here:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Thanks

---

