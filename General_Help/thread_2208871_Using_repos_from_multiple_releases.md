---
title: "Using repos from multiple releases"
date: 2014-03-02
forum: General Help
---

### Post by Tristan_Williams on 2014-03-02
I am running Ubuntu Minimal 13.10, so obviously I use the Saucy repositories.

Would it be ok to use the Trusty repos?

If yes, how would this affect my system? Would it cause any instabilities or package conflicts?

---

### Post by deadflowr on 2014-03-02
Package conflicts.

At this point, lots of them.

You can, however add like a ppa for stuff which is very isolated and doesn't need or have any dependency issues with the rest of the system.

---

### Post by Tristan_Williams on 2014-03-02
Thanks :) I guess I'll just wait for Trusty to be released

---

### Post by ian-weisser on 2014-03-02
> **Tristan_Williams said:**
> If yes, how would this affect my system? Would it cause any instabilities or package conflicts?

It could break your system. Don't do it.
We see plenty of problems in this forum from people who have foolishly or erroneously mixed releases.

1) Dependency problems. A 14.04 package may depend on other packages (or versions of other packages) that are not available in 13.10. This leads to a "partial upgrade" path that can break your system. Don't do it.

2) Compiled software. Many 14.04 binary packages are compiled against 14.04 toolchains, and rely upon 14.04 binary libraries. They are completely incompatible with the 13.10 versions, even though it's possible to force their installation using the package manager. Really don't do it.

3) Shell scripts and other interpreted (not compiled) packages can often be installed without a problem. But you need to check the source to determine the type of code. The package manager won't know and has no way to find out. On the other hand, lots of system-critical code that runs at startup/login/suspend/resume/logoff/shutdown is scripted, and changes often in response to system changes and bugs. Introducing system scripts intended for a different release of Ubuntu may break your system in new and interesting ways.

Personally, I would install software manually or using a PPA before I would mix packages from different releases.
Whenever you use a PPA or manual install, keep track of it. You will need to uninstall that software someday, and need to know how.

---

