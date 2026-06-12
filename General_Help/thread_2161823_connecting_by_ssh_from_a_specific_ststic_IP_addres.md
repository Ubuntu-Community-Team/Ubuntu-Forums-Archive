---
title: "connecting by ssh from a specific ststic IP address"
date: 2013-07-12
forum: General Help
---

### Post by lex1 on 2013-07-12
If I need to ssh into a remote server but only from a specific static IP address what chages need to be made in files 
allow acess and dany access

thanks
lex1

---

### Post by newbie-user on 2013-07-12
Not quite sure what you're asking regarding allow/deny permissions. However, regarding ssh, if you want to connect from a single static IP, then you would edit your firewall on your server to allow ssh from only that static IP.

If you use iptables, then something like
[code]iptables -A INPUT -s (your static ip)/(subnet slash notation) -i (external interface) -p tcp -m tcp --dport 22 -j ACCEPT

---

