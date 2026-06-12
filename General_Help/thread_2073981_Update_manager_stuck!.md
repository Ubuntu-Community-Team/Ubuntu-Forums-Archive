---
title: "Update manager stuck!"
date: 2012-10-20
forum: General Help
---

### Post by bonebrain on 2012-10-20
Last night I ran update manager, and it started to download a whole lot of stuff. OK, done it before, no problem. But because it was taking a long time, I interrupted it, thinking, ah, it'll remember what it downloaded and carry on from there today. Today I also unchecked several non-critical items, and update manager started downloading. After downloading 25Mb of 22Mb  (!) of Linux firmware (!) it returned a message stating that it could not download .... - "check your internet connection". After rebooting, I now get this error message as soon as Update Manager is started, internet connection is perfect, as usual. Sounds like I pressed a wrong button somewhere, I guess the interrupting of the UM. I suppose I could re-install Ubuntu - sounds a bit excessive, or just carry on with what I've got.

---

### Post by bonebrain on 2012-10-20
If I re-install Ubuntu, will it zap all my app stuff, or just the operating system files?

---

### Post by Frogs Hair on 2012-10-20
Hello and Welcome 

Try running the following in the terminal and report any errors here.```
sudo apt-get update && sudo apt-get upgrade
```The command is the same as running the update manager.

---

### Post by bonebrain on 2012-10-20
Thanks Frogs Hair, the command line instruction ran straight away, still running and notifying. I'll get back if it nosedives, but I gut a feeler it's gonna work. Always trust a command line.

---

