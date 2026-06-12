---
title: "Syslog pollution still with us after upgrade to 20.04.1"
date: 2020-10-18
forum: General Help
---

### Post by David_Partridge on 2020-10-18
Isn't anyone ever going to fix this idiotic bug - it is so infuriating:   Here's a not atypical set of messaes in syslog:

```

Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[6Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:31 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:35:11 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:35:11 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:35:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:35:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
93]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:32:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:33:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:00 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:10 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:30 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:40 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:34:50 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:35:11 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:35:11 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:35:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Oct 18 16:35:20 charon systemd-resolved[693]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.


```

If it isn't a bug - I'd very much like to know what's causing it and what the correct solution is.

---

### Post by David_Partridge on 2020-10-18
I'm trying to nail the requesting application down and this *may* be relevant:

[https://forum.transmissionbt.com/viewtopic.php?f=2&t=20566](https://forum.transmissionbt.com/viewtopic.php?f=2&t=20566)

David

---

### Post by David_Partridge on 2020-10-19
I asked about these messages on the systemd-devel mailing list - Lennart Poettering says that there's not such message in the upstream codebase:

> We have no such log line upstream. This must be a downstream change (Ubuntu?).
 


So please will you Ubuntu folks consider removing this log message or maybe issue it once for every 100 (or maybe 500) occurrences of the situation.

I am seeing thousands of these every day.

David

---

### Post by ActionParsnip on 2020-10-19
[https://superuser.com/questions/1372600/error-in-ubuntu-server-server-returned-error-nxdomain](https://superuser.com/questions/1372600/error-in-ubuntu-server-server-returned-error-nxdomain)

Does that help

---

