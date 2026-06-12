---
title: "Software Updater removed old kernels?"
date: 2019-06-05
forum: General Help
---

### Post by 2CV67 on 2019-06-05
I just ran Software Updater to install kernel 4.18.0.21 & was surprised to see it deleted old kernel 4.18.0.18. (but at least left old kernel 4.18.0.20)

In all my years Ubuntu-ing, this never happened before.
I don't think I changed anything.
I really prefer to remove old kernels myself.

Is this a new "feature"?

Can I cancel it somehow?

Thanks!

---

### Post by dino99 on 2019-06-05
Apt now manage the kernel list to avoid /boot being fulfilled with outdated entries. Default is now: latest + previous kernels.

---

### Post by PaulW2U on 2019-06-05
> **2CV67 said:**
> Is this a new "feature"?
According to the change log:
```
update-manager (1:18.04.8) bionic; urgency=medium

  * Offer removal of unused autoremovable kernel packages
    (LP: #1624644, #1675079)

 -- <redacted> <redacted@ubuntu.com>  Wed, 21 Mar 2018 14:34:05 +0000

```
I wasn't aware of this either until a post on these forums a few days ago. But then I always update using apt commands so this was a change or enhancement that went unnoticed for over a year.

---

### Post by CatKiller on 2019-06-05
apt has had this feature for a long time. The configuration was too conservative in 14.04, which was part of the issue with the boot partition being too small for that release. It's been fine for later releases.

The change to the Update Manager is only that it exposes that already-existing function from the underlying package management.

---

### Post by deadflowr on 2019-06-05
> Can I cancel it somehow?

Uncheck 'em from the removal listing.

I posted about this just yesterday:
[https://ubuntuforums.org/showthread.php?t=2420393&p=13863950#post13863950]("https://ubuntuforums.org/showthread.php?t=2420393&p=13863950#post13863950")
so, timely?

---

### Post by cruzer001 on 2019-06-05
Or take it a step further and cancel out update-manager, either in startup or /usr/bin/ and use Synaptic PkMgr.

---

### Post by Guy_Rouillier on 2019-09-08
I have sort of the opposite request.  I don't do anything fancy with kernels, so I'm quite happy to let Software Updater manage the kernels.  I just tried to run Software Updater and it failed due to lack of space on /boot.  But looking at the list of planned activities, Software Updater planned on removing an old kernel.  If it had done that *first*, it would not have failed in applying updates.  So, rather than delete kernels manually (which I've been doing for decades), I unchecked the first two sections in Software Updater, so that it only applied the kernel maintenance actions.  Then I reran it, and it installed new updates successfully.

I realize the risk here is that by removing old kernels first, there's a chance that updates may fail for some reason, leaving me with one less kernel than I started with.  But this risk seems minimal, since it maintains the current kernel plus 2 old ones.  So, at worst, I end up with current kernel plus 1 old one.  Seems pretty harmless, and better than the experience I had above.

---

### Post by Artim on 2019-09-08
I would *manually* remove previous kernels if they were taking up a lot of space (too much for an update, for example), leave the current kernel and *one* previos kernel in place, then run the updater with the option to manage the kernel.  The risk of having previous kernels removed first is too much. and I'd end up relying on previous snapshots of the system (Timeshift) to restore everything.

---

