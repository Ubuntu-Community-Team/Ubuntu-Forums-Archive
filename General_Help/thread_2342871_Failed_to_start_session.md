---
title: "Failed to start session"
date: 2016-11-10
forum: General Help
---

### Post by Mark Phelps on 2016-11-10
Geat ... FINALLY got Updates working by disabling IPV6 earlier today.

And now, a few hours later, can't login to my Ubuntu 16.10 Mate instance anymore -- get "failure to start session" in the login window.

Tried the advanced startup options, including repairing broken packages, and no change.

Tried searching on this, but I believe that a new startup process is being used in 16.10 and the old fixes don't work anymore.

I'm posting this from my Mint distro -- it still works OK.

I was able to view the lightdm log but it was very long and to generate a new log, for only this problem, I removed the file.

But when I rebooted Ubuntu, no new lightdm log was generated.  great!

UPDATE: Discovered this problem was due to deleting LOTS of packages in response to an apt remove command that I was told would fix a minor Firefox problem.

It does do that, but then it breaks the install so bad it won't run anymore.

Fixed the problem by restoring from backup I had made earlier using Clonezilla.

---

