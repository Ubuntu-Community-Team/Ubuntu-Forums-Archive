---
title: "&quot;Filter failed&quot; for HL 2240 Printer"
date: 2019-05-10
forum: General Help
---

### Post by raleigh3 on 2019-05-10
When I try to print to my Brother HL 2240, I get

```
Printer state message is: 'Filter Failed."

```
I then tried

```
su -c 'journalctl -u cups.service --since="None" --until="2019-05-10 16:28:51"' > troubleshoot-logs.txt
Password: 
su: Authentication failure

```

---

