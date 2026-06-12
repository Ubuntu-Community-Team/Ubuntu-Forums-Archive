---
title: "Unknown Hostname"
date: 2008-01-24
forum: General Help
---

### Post by cmoss28 on 2008-01-24
I've been trying to get Glassfish running under Eclipse and NEtbeans. No joy on either. Seems to be a problem with the server trying to resolve the hostname of the computer when starting the server. Upon further investigation I found that I cannot get the hostname of the computer to resolve. Even if it is in the /etc/hosts file. Anyone have an idea as to why it won't use the /etc/hosts file. The nsswitch.conf file has 'files' list first.

---

### Post by scxtt on 2008-01-24
what about the contents of **/etc/hostname**?

---

