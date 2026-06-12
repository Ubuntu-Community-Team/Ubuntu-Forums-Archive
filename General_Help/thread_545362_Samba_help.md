---
title: "Samba help"
date: 2007-09-07
forum: General Help
---

### Post by Bothered on 2007-09-07
I'm trying to share a directory using samba, but I'm new to it and don't know which options I should be using. I'm trying to share a directory, but I want access to the shared directory to be as limited as possible. The relevant section of /etc/samba/smb.conf is:

```
[Share]
comment = Shared directory
path = [path]
available = yes
browsable = no
public = no
printable = no
valid users = [me]
writable = yes
```

As I understand it, this will share the directory at [path] such that only user [me] can access it. Is there any way that I can lock it down tighter than this? Can I,for example, limit access to only certain ip addresses? Or are there other options I haven't thought of that would limit access even further?

---

### Post by reckless2k2 on 2007-09-07
well you can make that share viewable to only you on the system using chmod, chown, and chgrp. other than that, you can lock down communication from IPs via iptables. but i think that will lock only that IP to be able to access samba in general. best thing is to make the share on that host viewable on that system to no one but you as well if not already the case. 

query changing permissions.

---

### Post by Bothered on 2007-09-09
Yes, that's already the case. I was wondering if it is possible to make that share accessible to only a certain machine, such as localhost (I'm using samba to share files with virtualised OSs), while still having the other shares accessible to the rest of the network?

---

### Post by scxtt on 2007-09-09
from **man smb.conf**:

hosts allow = 150.203. EXCEPT 150.203.6.66

---

### Post by Bothered on 2007-09-09
That looks like it, thanks. I have been through a good bit of that man page but didn't find that.

---

