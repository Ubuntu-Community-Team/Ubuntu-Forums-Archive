---
title: "Setting memory Limits"
date: 2007-03-15
forum: General Help
---

### Post by BatteryCell on 2007-03-15
Hey everybody, I just needed to set some memory limits (max allowed memory to 4 megs) for a user yet I cannot seem to do it.  
```

ulimit -v 4096

```
Sets it for a single process, but the user can simply make the process sleep, stick it in the background, and then run more of em (eventually crashing the computer).

I have played a little with pam but haven't been able to really get anything to work.

Any help would be greatly appreciated :-) 

Thank you,
Joe

---

### Post by Levander on 2007-03-15
This may be complete overkill for what you're doing, but there are VPS's.  You could give each user one VPS which can have memory limits set on it.  Each VPS on a computer basically runs an independent instance of the operating system.  The commonly used free one on Linux is xen.  There are packages for it in the Edgy.  Although, I vaguely remember Ubuntu was going to have better support for Xen in Feisty.

---

### Post by hashbrowncipher on 2007-03-15
I'm working with Joe on this project, and I can say that VPS's would be "complete overkill."   We're working on a semipublic server, but we are worried that a badly coded program or a malicious program could sap all of its available memory.  Thank you for your suggestion though.

Josh

---

