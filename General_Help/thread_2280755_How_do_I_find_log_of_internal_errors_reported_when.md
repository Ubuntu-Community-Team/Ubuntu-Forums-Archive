---
title: "How do I find log of internal errors reported when booting?"
date: 2015-06-02
forum: General Help
---

### Post by dora5 on 2015-06-02
My system popped up twice with "sorry, Kubuntu has experienced an internal error" after logging in, but didn't then bring up the box to report the error.    What log file tells me what the errors were?   

I had my system mysteriously hanging on me, so I looked at the boot log and uninstalled OpenBox.   It appeared to reinstall GRUB, and it appeared to find all three installations on both hard drive, which is the first time GRUB has ever managed that piece of magic.   Appeared to boot up and work normally but I found it crashed this morning.   None of hte logs I've looked in contain any clue.   Not apport.log (which is empty), apport.og.1, which has information from two days ago, kern.log, dmesg.   Where do I look?

---

### Post by DuckHook on 2015-06-02
try *syslog* as well. *dmesg* is only for current session and is not persistent over multiple sessions. *apport.log* won't show anything if crash does not invoke apport. *kern.log* only shows kernel events and won't log a crash that is external to the kernel, as yours seems to be.

I am rather concerned that you nuked OpenBox. It should not be necessary, and we don't know what dependencies may be broken with it's disappearance. GRUB probably self-updated after your tinkering which might account for its sudden recognition of additional OSes. You can manually force it to do the same thing whenever you want with:```
sudo update-grub
```Hate to go this far, but you might wish to just backup all data and reinstall a pristine OS. It would appear that you've tinkered with it now way past its default config, and you will have issues at the next upgrade or possibly even with routine updates. It's also going to be more difficult tracking down issues because you are missing pieces of the default install. It may just be my penchant for having things orderly, tidy and in their proper place, but I would find a system so far from the norm to be very discomfiting.

**Addendum**

Just reread you post more carefully. You are using Kubuntu, which I am not that familiar with. I do not think that Kubuntu comes with OpenBox. Did you install this afterwards? If so, then you are mixing DEs which is always an invitation for the sort of wonky behaviour that you are experiencing. Anyways, I may be jumping to conclusions here because I really don't know much about Kubuntu, but the warning about mixing DEs is still very valid and something you should heed.

---

