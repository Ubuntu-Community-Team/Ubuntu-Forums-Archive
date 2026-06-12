---
title: "Problem with firewall of Samba running"
date: 2006-07-27
forum: General Help
---

### Post by leeyee on 2006-07-27
Hi guys,

I'm about to setup a samba server for our local network, and I don't want to shutdown the firewall on the server. So I'm here asking you guys a question, how can I allow samba accessing from those clients with firewall running?

Maybe this:
```

iptables -A INPUT -p UDP --dport 137,138,139 -j ACCEPT

```
will work? I'm not sure about this, I'm quite new to iptables and even don't know how to save changes on it.

And I dare not to do any changes for samba before I understand it correctly. Thank you guys! Thank you for your replies!

Best regards,
leeyee

---

