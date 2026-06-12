---
title: "Problems with kernel updating and nvidia-glx"
date: 2007-03-15
forum: General Help
---

### Post by chuckyp on 2007-03-15
Not really sure if I should report this as a bug or not so i'm asking your opinion.

I've noticed that if a user has nvidia-glx installed which requires linux-restricted-modules-`uname -r` and the kernel updates.  The linux-restricted package doesn't update for the new kernel.  If the user restarts after the kernel update with out installing this package the kernel module will fail to load borking X.  Until they install the apropriate resticted modules for the new kernel.

This could be fixed by updating nvidia-glx when a new kernel comes out removing the dependencies for the older linux-restricted modules.  It would make the system install the new version as well.

Like I say not sure if this could really be considered a bug or if it is this way for a reason.  It just seems a little odd to me to expect the end user to be able to figure all this out on their own rather then just have it work via update-manager.

---

### Post by chuckyp on 2007-03-16
I've noticed with the newest updates to fiesty if someone doesn't install the specific restricted it dfeaults to something and prompts on reboot to enable teh driver.  Trying to confirm this.

---

