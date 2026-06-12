---
title: "Compiz pooped out on me"
date: 2008-05-19
forum: General Help
---

### Post by Gambini on 2008-05-19
After the new installation of 8.04, compiz/emerald has stopped working. I did ```
sudo apt-get install compiz
``` and it was at the newest version, so then I did ```
compiz--replace
``` and got ```
gambini@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

I am using an 8800GT, but I am not really sure how to check what driver I am using for it. I used envy in Gusy, and I think I used the restricted drivers manager thing for Hardy. Any help appreciated.

EDIT: a few minutes later, the terminal was still open and it added a few lines:
```
ambini@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2400021 (gambini@ub)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x2400021 (gambini@ub)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

```

EDIT 2: It's all good now. I just had to reinstall the driver. Thanks everyone for not helping me:lolflag:(jk)

---

