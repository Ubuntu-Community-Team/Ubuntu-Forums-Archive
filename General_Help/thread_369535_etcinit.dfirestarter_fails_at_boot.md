---
title: "/etc/init.d/firestarter fails at boot"
date: 2007-02-24
forum: General Help
---

### Post by casaschi on 2007-02-24
I'm using Edgy.
At boot, the script "/etc/init.d/firestarter start" fails (can see that in /var/log/boot).
As a result, no configuration for iptables is loaded at startup (as shown by "sudo iptables -L -n").

If I manually start firestarter, after logging in as a user, either from a terminal ("/etc/init.d/firestarter start") or from the admin gui, then "sudo iptables -L -n" shows me all firewall rules in place.

What is wrong with my system?
Only thing I can think of is that my "external" interface wlan0 comes up only later in the boot process, so there is no external interface up when the firestarter script loads at boot.

Any suggestion?

-- Paolo

---

