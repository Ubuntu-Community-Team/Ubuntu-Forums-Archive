---
title: "New Edgy updates"
date: 2007-02-08
forum: General Help
---

### Post by drpaul on 2007-02-08
Update-manager announced 2 updates this morning, but the update-manager info window shows 5 of which only 2 are checked.

They all deal with linux header kinds of things, and I'm concerned about updating some to a new level and leaving some at the old level.

Why would update-manager select only some of the available updates?

TIA

Paul

---

### Post by Kalinda on 2007-02-08
I have the same problem... for me, Adept says that linux-headers-generic and linux-image-generic will break if updated. Normally, though.. if you update and something is broken, apt will resolve your problem by downloading what the broken package needs.

I'm going to try it, since I can always downgrade if there's no way to fix it.

EDIT: Ok, I can't even actually update them. For one it says:
```
linux-image-generic:
 Depends: linux-image-2.6.17-11-generic  but it is not installable
```

I can only assume this means they're meta packages and the updater can't download the next version of the real package because it doesn't exist. However, I use the 386 kernel, not the generic one. Would it actually be safe for me to remove the generic one? Or should I be using it? Is there even a difference?

---

### Post by banditti on 2007-02-08
This is just a suggestion, but there are quite a few threads about this, can we consolodate?  this has the most posts:

[http://ubuntuforums.org/showthread.php?t=356257](http://ubuntuforums.org/showthread.php?t=356257)

---

### Post by drpaul on 2007-02-08
Works for me. I read some, and my view is wait until this ugly situation gets cleaned up.

Paul

---

