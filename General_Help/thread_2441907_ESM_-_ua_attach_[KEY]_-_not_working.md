---
title: "ESM - ua attach [KEY] - not working"
date: 2020-04-27
forum: General Help
---

### Post by jumb0eadg on 2020-04-27
When I do ```
sudo ua attach 
```, the command prompt hangs and I get the following error after some time:
```

Failed to connect to authentication server
Check your Internet connection and try again
```

The server has connection and the outgoing iptables is set to accept.
Any help is appreciated.
Thank you.

---

### Post by jumb0eadg on 2020-05-05
[solved] Looks like somehow the iptables was blocking connection, even though the OUTPUT was set to ALLOW.
I had to flush all iptables rule and add 'ua' and then re-add all iptables, and finally ua attach worked.

---

