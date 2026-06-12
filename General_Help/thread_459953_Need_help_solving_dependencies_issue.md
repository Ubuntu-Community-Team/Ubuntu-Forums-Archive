---
title: "Need help solving dependencies issue"
date: 2007-05-31
forum: General Help
---

### Post by DougieFresh4U on 2007-05-31
I need to know what will solve the following. Two days ago I 'borked" another machine playing with kernels in Synaptic and I don't need to "bork" this one :)

[B]The following packages have unmet dependencies:
  linux-backports-modules-generic: Depends: linux-backports-modules-2.6.20-16-generic which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
linux-backports-modules-generic [2.6.20.15.14 (feisty, now)]

Score is 0

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-backports-modules-generic

Score is -301

Accept this solution? [Y/n/q/?] [/B]

Thanks

---

### Post by kwaanens on 2007-05-31
I have the same issue.  linux-backports-modules-generic is a metapackage, making you sure you install backported modules for your kernel if you need them. Your latest version of backports-modules is 2.6.20.15. (EDIT: I see you're going directly from -14 to -17. -14 is no longer in the repos, -15 is. -16 is a security update, in the security repos enabled by default. Try installing both -15 and -16, boot with -16. If you get some errors like in [this thread]("http://ubuntuforums.org/showthread.php?t=456662"), boot with -15 instead, until there's a -17 available.)

When/if you're running 2.6.20-16 the backported modules are not running. Do as me, just leave these meta-packages alone untill there's an upgrade to -16 of them, if they are coming. If you're running -16 with no problems, you have no problems (I know, that sounds redundant :) )

Some people (a thread 37 pages long) are reporting problems with -16 kernel, so there's likely a -17 upgrade soon anyway.

Moral is: if your computer works after updating and rebooting (if we're talking kernel or module updates), you're not having a problem. If you have a problem, post a bug report, or add to an existing one!

- Ketil

---

### Post by DougieFresh4U on 2007-05-31
Thanks kwaanens for reply
No problems booting so I think I will just ignore and not adjust ANYTHING until updates come along :popcorn:

---

### Post by kwaanens on 2007-05-31
As long as you only use the repos you're for the most part safe. Don't go recompiling for fun :)

- Ketil

---

