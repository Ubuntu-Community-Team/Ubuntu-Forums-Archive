---
title: "system updates / sudo does not ask for passwords anymore"
date: 2013-10-02
forum: General Help
---

### Post by bluepicaso2 on 2013-10-02
hey there,
So its like, I am noticing things.
first system updates previously required to enter passwords, but not it does not. Simply clicking on "install updates" starts the process.
also Sudo commands don't require passwords any more.

I wanted to know how can i revert this to normal.

I am the only user to the system.

---

### Post by TheFu on 2013-10-02
open a terminal.
**$ sudo visudo**
Is there a line with "NOPASSWD" in the file?

Or the timeout for sudo could have been increased beyond the 5 minutes?

Or someone finally decided to create a Linux specific virus that abuses sudo?

---

### Post by BBQdave on 2013-10-02
> **bluepicaso2 said:**
> first system updates previously required to enter passwords, but not it does not. Simply clicking on "install updates" starts the process.

After first install, Ubuntu asks for password for first updates to newly installed system. Then it no longer asks for password, unless it is a Kernel Linux update :)

---

### Post by grahammechanical on 2013-10-02
Also, when we run several sudo commands one after the other we only need to enter the password once. This feature will time-out after we stop using sudo commands.

---

