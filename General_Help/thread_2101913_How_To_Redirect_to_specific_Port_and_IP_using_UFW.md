---
title: "How To: Redirect to specific Port and IP using UFW"
date: 2013-01-05
forum: General Help
---

### Post by tantrex on 2013-01-05
I have UFW setup on my dedicated box, and it has 3 IP Addresses associated with it like below(Not real ips). 

127.0.0.2 (eth:0)
127.0.0.3 (eth:0:1)
127.0.0.4 (eth:0:0)

I am having in coming traffic into 127.0.0.[COLOR="red"]4[/COLOR]:9555 and want to redirect it too 127.0.0.[COLOR="red"]4[/COLOR]:1234.  The traffic is going 127.0.0.[COLOR="Red"]2[/COLOR]:1234(default eth:0 ip) instead.

Here is the setup im using in the /etc/ufw/before.rules file:
```
*nat
:PREROUTING ACCEPT [0:0]
-A PREROUTING -p tcp --dport 9555 -j REDIRECT --to-port 1234
COMMIT
```

Is there any way I can get it to stay on the same sub ethernet interface or am I basically just SOL?

Thanks,
tantrex

---

