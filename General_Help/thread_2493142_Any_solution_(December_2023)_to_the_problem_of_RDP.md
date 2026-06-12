---
title: "Any solution (December 2023) to the problem of RDP into PC with autologin?"
date: 2023-12-05
forum: General Help
---

### Post by uacnt83982803 on 2023-12-05
So I know this is/was a problem.  I have 2 Ubuntu 22.04 machines and periodically RDP from one to the other to install updates, etc.  Works great until an update requires a reboot.

After the reboot, as we know the auto login does not unlock the keychain, so the target pc changes the RDP username and password combination.  Which requires physical access to the other machine (to set it back the way I had it) which I am trying hard to avoid.

Is there any solution to this yet?

---

### Post by TheFu on 2023-12-05
Don't use RDP, use **x2go** instead. [https://wiki.x2go.org/doku.php/doc:newtox2go](https://wiki.x2go.org/doku.php/doc:newtox2go)

---

### Post by uacnt83982803 on 2023-12-05
Ok thanks friend I will give it a go.

---

