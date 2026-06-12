---
title: "Have to fix DNS failure after every reboot (22.04)"
date: 2023-05-03
forum: General Help
---

### Post by beriksson on 2023-05-03
Every time I reboot Ubuntu, my DNS doesn't work. After running the following commands in sudo mode, everything is fine until I restart again.

```
rm /etc/resolv.conf
ln -s /run/resolvconf/resolv.conf /etc/resolv.conf
resolvconf -u

```

What can I do to solve this permanently?

---

### Post by TheFu on 2023-05-03
First, resolvconf is deprecated and has been for awhile.  By using it, you aren't doing it the way 22.04 expects.  

I think by default, 22.04 uses systemd-resolved instead, but I could be wrong.  Server and Desktop installations are different when it comes to network setups, so that could be different.

There is a resolved.conf file, which is how 22.04 systems should be configured.  There's a manpage that explains the different settings, but they are commented inside the file and easy enough to understand.  I suspect just 2-3 lines need to be modified, then tell resolved service to restart.

Of course, neither of those are really needed and if you run DNS on your LAN, there's little need for them at all.  Just disable both resolvconf and resolved, then delete the /etc/resolv.conf symlink and create a proper  /etc/resolv.conf file with the 2-3 lines you want ... like we've done since the early 1990s.

---

