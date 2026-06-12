---
title: "Enforce password for target account when using &quot;su -&quot;"
date: 2023-04-27
forum: General Help
---

### Post by strungoutfan78 on 2023-04-27
I got myself into a weird situation.  I've been implementing AD bind + DUO auth on all of our Linux servers.  Works a treat, but an unintended side effect of this is that now, if I sign in as root, then issue a "su - <any_domain_account>", I can switch to that AD account without entering a password, regardless if the user has ever authenticated from this device.  This seems highly unsecure to me but I'm not sure exactly how to fix it.  It also doesn't make any sense to me that a user can auth against AD without entering a password.

---

### Post by TheFu on 2023-04-28
root can do anything in a system that doesn't use role-based administration, which Ubuntu does not.
In short, working as designed.

---

