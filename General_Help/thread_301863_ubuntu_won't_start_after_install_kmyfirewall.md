---
title: "ubuntu won't start after install kmyfirewall"
date: 2006-11-17
forum: General Help
---

### Post by ljk25 on 2006-11-17
Hi, I'm new in ubuntu, just install kmyfirewall recently and now my ubuntu won't start. before i restart, kmyfirewall warn me something like that may happen and give me an instruction to solve this but unfortunately i didn't copy it down (me bad.. to lazy), can anyone help me to solve this? thanks in advance.

---

### Post by ljk25 on 2006-11-22
Manage to fix it myself. The problem is due to iptables not kmyfirewall. An invalid setting done using kmyfirewall cause the problem. have to uninstall iptables first in recovery mode, then uninstall kmyfirewall. after that, reinstall iptables and use arno-iptables-firewall to re-setup iptables.](*,)

---

