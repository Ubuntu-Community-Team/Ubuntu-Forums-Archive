---
title: "Login and su - fail"
date: 2012-10-15
forum: General Help
---

### Post by TheEffigy on 2012-10-15
Hi, 

After messing around with pam and fuse a bit I seem to have broke the ability to su. 

I can "su user" but cannot "su - user" any longer. Also "login" now fails with authentication failed. 

In the log I can see permission denied on changing permissions of the pseudo terminal.

Any thoughts on how to begin figuring this out?

SSH and everything else seem to work just fine I should note.

---

### Post by TheEffigy on 2012-12-04
For posterity I should mention I fixed this. 

Using strace on 'strace su -' I discovered that /etc/pam.d/su-l' was missing! Adding it resolved the issue.

---

