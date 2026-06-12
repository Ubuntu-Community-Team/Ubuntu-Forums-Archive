---
title: "&quot;dpkg --configure -a&quot; stuck/hanging"
date: 2017-06-25
forum: General Help
---

### Post by jack137 on 2017-06-25
Hi,

While updating a machine this morning I've had something happen that's never happened before - apt upgrade "froze".
After giving it about 40-50 mins I concluded it's fully frozen, and I killed the process from another terminal as the initial terminal wasn't responding to ctrl+c.

Obviously now the apt database is locked and I'm unable to run apt upgrade, so I ran dpkg --configure -a - and it seems to be hanging on this:
```
root@src-eu05:~# dpkg --configure -a
Setting up grub-common (2.02~beta2-36ubuntu3.11) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults

```
I've done some pretty extensive research but I can't find much relating to the specific issue I'm having, and I'm not even sure if the issue is with grub specifically. I want to avoid unnecessary downtime and mistakes so I figured I'd see if anyone here could offer any advice?

Thanks for your time

---

