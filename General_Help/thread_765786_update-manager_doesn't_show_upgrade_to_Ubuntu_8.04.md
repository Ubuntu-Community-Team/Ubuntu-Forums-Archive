---
title: "update-manager doesn't show upgrade to Ubuntu 8.04 release version"
date: 2008-04-24
forum: General Help
---

### Post by jery_wang2002 on 2008-04-24
I am using Hardy Beta-RC and always updated. Hardy is already release but I have yet to see my update-manager shows Release upgrade.

I have pressed Checked but update list always empty. 

What have gone wrong?

---

### Post by noynac on 2008-04-24
By updating Hardy beta, you now have Hardy final. You don't need to do anything.

---

### Post by kostkon on 2008-04-24
Indeed, you are already using the final version.

If you want to be sure, just go to *System -> Administration -> System Monitor* and check what it says in the *System* tab. You can also check your *Ubuntu* version by opening a terminal and giving:
```
lsb_release -a
```
If the output says *Release: 8.04* then you are OK.

---

