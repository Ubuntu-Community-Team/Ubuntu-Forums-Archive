---
title: "KeepassX question"
date: 2019-08-12
forum: General Help
---

### Post by ra7411 on 2019-08-12
I read on some security write up that it's best not to have Keepass open and running when you're not using it, since it's possible for some online or in the computer intrusion to read unencrypted log-ins.

Any truth to that?

Thanks

---

### Post by TheFu on 2019-08-13
The only major issue I know, which really applies to all programs, including password managers, is that someone who gains root or sudo privileges can search all of the process for login credentials.  Again, this attack applies to all running processes.  When I saw the attack, I did it on my machine to verify it.  The fix for any password manager is to close the DB relatively quickly after use and overwrite any data in RAM that formerly held unencrypted data.  I know keepassxc does that. Perhaps regular keepassx does now too, but I don't know.

If the DB is unlocked, then parts of the DB are in RAM, which can be read.

I moved from KeePassX to KeePassXC about 18 months ago because the XC version appears to have more active development and has added support for some security features I planned to use.

---

