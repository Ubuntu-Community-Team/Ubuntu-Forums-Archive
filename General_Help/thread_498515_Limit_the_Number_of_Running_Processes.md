---
title: "Limit the Number of Running Processes"
date: 2007-07-11
forum: General Help
---

### Post by Billybob on 2007-07-11
How would I limit the number of processes a certain user can have running? I want to do it on a per-user basis, not global and not the same for every user.

Danke!

---

### Post by stylishpants on 2007-07-11
In your /etc/profile, add a few lines of shell to set ulimit -u based on the username or group membership.

IIRC, once you use ulimit to set a limit within an instance of a shell, that limit cannot be reset, so your users wouldn't be able to change it.  You should probably verify that though.

Of course you'd need to address the case where your user isn't using bash.  You may need to implement your decision logic in the system-wide scripts for tcsh, zsh and friends too.

---

