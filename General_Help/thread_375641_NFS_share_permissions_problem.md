---
title: "NFS share permissions problem"
date: 2007-03-04
forum: General Help
---

### Post by imjustabill on 2007-03-04
I have 2 nfs shares setup my box, my /etc/exports looks like this:

```
/stuff 192.168.1.1/24(rw,no_root_squash)
 /home/bill 192.168.1.1/24(rw,no_root_squash)
```

I can mount the /home/bill directory just fine, but the /stuff directory gives me a "Permission Denied" error when I try to mount it. The folder has 777 permissions, and my hosts.allow and hosts.deny are (temporarily) empty. Any ideas what I'm doing wrong?

---

