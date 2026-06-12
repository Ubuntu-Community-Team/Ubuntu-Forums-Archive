---
title: "Vuze/Azureus: Can't register"
date: 2007-11-17
forum: General Help
---

### Post by hanzomon4 on 2007-11-17
I'm trying to register a vuze account but I keep getting this error > Could not initialize the browser's security component. The most likely cause is problems with files in your browser's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the browser and fix the problem. If you continue to use this browser session, you might see incorrect browser behaviour when accessing security features.
Followed by this```
Firefox can't connect securely to www.vuze.com because the SSL protocol has been disabled.
```

How do I fix this?

---

### Post by hanzomon4 on 2007-11-17
I fixed it, I needed to sudo chown -R username:username ~/.mozilla/eclipse/

---

