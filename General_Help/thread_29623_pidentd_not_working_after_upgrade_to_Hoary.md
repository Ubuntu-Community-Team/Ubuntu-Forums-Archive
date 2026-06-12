---
title: "pidentd not working after upgrade to Hoary"
date: 2005-04-25
forum: General Help
---

### Post by Juergen on 2005-04-25
After the upgrade I now get this in /var/log/syslog with pidentd:
> Apr 24 14:28:06 localhost identd[10705]: started
Apr 24 14:28:06 localhost identd[10705]: netlink_lookup: write failed: Connection refused
I now installed gidentd and this works. 
I'm just interested if I should file a bug-report - has anybody else this problem or is it my installation?

---

