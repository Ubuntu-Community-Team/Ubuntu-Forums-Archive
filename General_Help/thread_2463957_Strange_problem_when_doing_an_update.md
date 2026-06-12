---
title: "Strange problem when doing an update ?"
date: 2021-06-22
forum: General Help
---

### Post by oden99 on 2021-06-22
Just ran an "update/upgrade this morning" and got the following result

"/usr/bin/deb-systemd-invoke: 32 =head1: not found
/usr/bin/deb-systemd-invoke: 39: Syntax error: newline unexpected"

Those two lines in a loop in Bash shell and after a while the loop got recognized by shell and I got a "want to send an error report?"

Did this break something in my setup ? or do I have a problem with the "policy-rc.d" from an earlier update event ?

I am not so familiar with the inner working yet but trying to learn..

---

### Post by Impavidus on 2021-06-22
There's something strange going on with /usr/bin/deb-systemd-invoke. Can you show the contents of that script? It might be damaged.

Also, which version of Ubuntu? And what was the other output you got from apt upgrade? It may be good to know what package was being installed when the problem occurred. If your terminal got flooded with output, it may be easier to see from the final lines in the log file:```
tail /var/log/dpkg.log
```

---

