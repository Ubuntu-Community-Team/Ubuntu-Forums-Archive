---
title: "HDD Corrupt after updating"
date: 2007-12-21
forum: General Help
---

### Post by mattinrom on 2007-12-21
I am running Ubuntu 7.10 Gutsy Gibbon.
I installed from I386 Live CD.
Fresh install and it listed 132 updates, i got the updates and rebooted
and when it came back up it said my / was unclean and ran fsck, then fsck died.
I did some detective work and saw a few points of interest, during shutdown with the splash screen off
right after the update it said mount: root is busy, (that caused the corruption) then i choose to install
a command line only system with the alternative disc, and ran apt-get upgrade to watch it closer
it downloads a kernal-image update, and gives a warning: lba32 assumed this is all i have, i need help
if anyone has any ideas.... i cant use any ubuntu based os, also i checked my hardware and installed debian-sid which is what im posting from... help plz thx

---

### Post by ronmonki on 2008-01-07
Think im having the same problem, all was fine then all over a sudden im getting corruption on everything I download? strange....

2.6.22-14-generic #1 SMP

Gutsy....

---

### Post by Rasputin_III on 2008-01-26
While I don't know about the fsck *failure* (or the recurring corruption as reported by ronmonki), I've traced the cause of unmountable / filesystem and subsequent fsck to the libc6 package downloaded from the gutsy-updates repository.

What I don't know, and the reason I haven't posted a bug report in launchpad, is if upgrading such a core (and immediately used) component will *always* result in a locked root filesystem.
If that is the case, then there is nothing that can be done about it other than minimizing the effect by sync'ing immediately before reboot--and a notice along those lines should be told to the user.
If, on the other hand, it's something avoidable by correcting the package--all the better.

Does anyone know which is the case?

Ras

---

