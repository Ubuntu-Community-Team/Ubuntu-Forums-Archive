---
title: "New Apt-get and Aptitude"
date: 2007-01-01
forum: General Help
---

### Post by Enkra on 2007-01-01
I know the difference between Apt-get and Aptitude is that Aptitude removes dependecies when you remove a package.

But I just read in this thread[http://ubuntuforums.org/showthread.php?t=20001&page=2]("http://ubuntuforums.org/showthread.php?t=20001&page=2")  that the new Apt-get in Edgy have **sudo apt-get autoremove** to remove no longer needed dependencies.  Question is does **apt-get autoremove** work the same as Aptitude? Anyone mess around with **apt-get autoremove** yet?

Couldn't find manual for apt-get autoremolve.

Thanks

---

### Post by bruenig on 2007-01-01
apt-get autoremove does pretty much work the same as aptitude. What happens is, when you apt-get remove a package, it won't remove the dependencies. It instead lists the dependencies and then tells you that if you wish to remove them that you can do apt-get autoremove. So the only difference is that apt-get doesn't force you to remove the dependencies and aptitude does.

---

### Post by aysiu on 2007-01-01
It works pretty much the same way, but *autoremove* is available only as of Edgy--not Dapper or Breezy.

---

### Post by Enkra on 2007-01-02
Cool, if **apt-get autoremove** work the same as **aptitude**, then I rather use **apt-get** because with **apt-get** you are more in control (**aptitude** force to you remove dependencies even if you don't want to).

As of before, the only reason to use **aptitude** over **apt-get** is the removal of packages with its dependencies, but with the new **autoremove** option in the new **apt-get**, there's no reason to switch to **aptitude**.

If this is incorrect, please let me know.

---

### Post by bruenig on 2007-01-02
> **Enkra said:**
> Cool, if **apt-get autoremove** work the same as **aptitude**, then I rather use **apt-get** because with **apt-get** you are more in control (**aptitude** force to you remove dependencies even if you don't want to).

As of before, the only reason to use **aptitude** over **apt-get** is the removal of packages with its dependencies, but with the new **autoremove** option in the new **apt-get**, there's no reason to switch to **aptitude**.

If this is incorrect, please let me know.

These are my sentiments exactly and is from my experience completely true.

---

