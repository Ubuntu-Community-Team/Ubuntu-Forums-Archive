---
title: "Per-user iptables scripting"
date: 2007-07-26
forum: General Help
---

### Post by imbjr on 2007-07-26
I'd like to setup an iptables login script for one user account on my PC - the other accounts do not require iptables management. 

So: How do I setup a login script to run for one user only, that will involve issuing of commands that would normally require sudo prefixing and therefore the typing in of a password?

---

### Post by imbjr on 2007-07-26
Found the solution - after quite a dig-about:

I discovered that iptables can support per-user filtering, so I enabled that. After a failed attempt at getting the iptable tables to restore at boot-time, I now just run the original iptable config commands at boot time, via init.d.

I was hoping there was a way of running a superuser-required command in an ordinary user's boot script - but I couldn't see a way of doing that. So, a global bootup script with per-user-specified filtering is the way.

---

