---
title: "Hardy Updates whacked restricted drivers?!?"
date: 2008-05-09
forum: General Help
---

### Post by splicer on 2008-05-09
I ran updates last night for Hardy, and now the three restricted drivers (sound, wifi, & modem) have disappeared and I can't seem to get them to come back.  After removing/reinstalling a number of packages via Synaptic, such as linux-restricted-modules-2.6.24-17-generic and it's ilk, I still have no results -- no sound, no wifi (don't care about the modem).

I'm at the end of my rope here ... anyone have any ideas?

---

### Post by forestpixie on 2008-05-09
Try reinstalling the previous versions available in the normal repos from synaptic - I believe that -17 is still in proposed - but I could be wrong.

---

### Post by yaknowwat on 2008-05-09
you can temporarily revert to an older kernel in grub. (press Esc as grub is loading)

I did this because i was experiencing problems with the new kernel because there were no modules for the updated kernel recently the modules for it have been coming in though.

---

### Post by splicer on 2008-05-09
Thanks for the suggestions.  I did finally get it fixed by following the hints found [here]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/208676"), which was a very similar problem.  

So I guess this indicates that there may still be a dependency problem in the kernel update process.

Count this as RESOLVED.

---

