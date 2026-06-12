---
title: "Where is the DN stored?"
date: 2005-07-04
forum: General Help
---

### Post by Dromio on 2005-07-04
When I set up my ubuntu PC, I had a dyndns domain, so somewhere during the install I told it the machine was "myolddomain.dyndns.org".  Since then, I've purchased my own domain.  I grepped  /etc for "myolddomain" and changed every entry I could find to my new information.

But when I just installed slapd, it still used myolddomain.dyndns.org in it's configuration.  Anyone know where it could have kept this?  I don't want to have to go back and check on this every time I install a new package.

---

