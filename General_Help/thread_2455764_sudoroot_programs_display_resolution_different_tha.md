---
title: "sudo/root programs display resolution different than normal user"
date: 2020-12-27
forum: General Help
---

### Post by imzack2 on 2020-12-27
I am opening up wireshark without sudo privileges, and it looks fine.

When I open wireshark with sudo/root access, the resolution must change the GUI, as it is extremely hard to read.

Any thoughts on how to make the root user have the same display settings as a normal user?

Thanks!

---

### Post by ActionParsnip on 2020-12-27
If you add your user to the wireshark group, then log off and on again you should be OK. Does running the application as your user (without sudo) do what you want?

---

