---
title: "saslauthd symlink issues"
date: 2006-08-14
forum: General Help
---

### Post by Vermyndax on 2006-08-14
Good morning!

I have a Ubuntu 6.06 server deployed with postfix, saslauthd, amavisd-new and the works.

I have a problem with postfix not seeing the saslauthd PID and whatnot - it's looking, no matter what I seem to do, in /var/run/saslauthd.

A tip on the forums somewhere had me put a symlink of /var/run/saslauthd --> /var/run/postfix/var/run/saslauthd.  This worked and solved the problem.

However, when the system is rebooted, the symlink gets destroyed and I have to manually put it back.

Any suggestions?  Can anyone help me figure out why postfix is looking in /var/run/saslauthd when many instructions have it set up in /var/run/postfix/var/run/saslauthd?

Thanks!

---

