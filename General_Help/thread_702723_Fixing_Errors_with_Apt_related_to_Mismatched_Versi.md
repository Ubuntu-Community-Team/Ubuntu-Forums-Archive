---
title: "Fixing Errors with Apt related to Mismatched Versions"
date: 2008-02-20
forum: General Help
---

### Post by BrentNewland on 2008-02-20
II've been fighting with ubuntu hardy for months now. Every time I run Apt-Get, I get loads of errors; when I checked Synaptic I would find packages being installed that are newer than the hardy versions, but that I couldn't locate in any repositories.

Well, turned out I had a file in /etc/apt/sources.list.d/ called emdebian.sources.list. This apparently contained newer Debian versions of Hardy files (which was causing a lot of problems for me). So I commented out everything in that file and did an apt-get update.

But that left me with a ton of packages mismatched. What to do? I created an /etc/apt/preferences file with the following:

Package: *
Pin: release a=hardy
Pin-Priority: 1001

and did an apt-get upgrade.

Only problem left now is that my system isn't recognised as Hardy when I use Add/Remove programs (something to do with just changing the repos to hardy and doing an apt-get upgrade instead of a Dist-Upgrade).

---

### Post by BrentNewland on 2008-02-21
Not sure why it was moved from tips... but that's all it is. Some advice that was hard to find on how to fix ubuntu when having different repos almost hosed it.

---

