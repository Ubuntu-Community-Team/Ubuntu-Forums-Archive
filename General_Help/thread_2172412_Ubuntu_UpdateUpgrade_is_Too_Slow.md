---
title: "Ubuntu Update/Upgrade is Too Slow"
date: 2013-09-04
forum: General Help
---

### Post by tokyo-joe on 2013-09-04
I am running several ubuntu-based systems (Ubuntu 13.04 Raring and Linux Mint 15 Olivia).

All those systems take VERY long time (such as 30 minutes) to update/upgrade when I execute "sudo apt-get update" or "sudo apt-get upgrade". All systems get stuck at retrieving from "archive.ubuntu.com (2001:67c:1360:8c01::18) ". Other repositories seem okay.

I see it has started a couple of weeks ago.

Why is it taking so long and how can I fix it?
Is it a repository server problem or a machine problem? (I think the possibility is the server problem, because it started on multiple boxes almost at the same time).

---

### Post by tokyo-joe on 2013-09-04
The problem self resolved.
The workaround is here: [http://www.bearfruit.org/2013/05/06/ubuntu-server-having-ipv6-probs-its-easy-to-disable/](http://www.bearfruit.org/2013/05/06/ubuntu-server-having-ipv6-probs-its-easy-to-disable/)

In short, disabling ipv6 network connection resolves the issue. But I am not sure how it works and why it has started a couple of weeks ago.

Can somebody tell how this workaround helps?

---

