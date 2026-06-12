---
title: "Why is apt-get wanting to upgrade things that are already at the latest version?"
date: 2007-12-24
forum: General Help
---

### Post by besson3c on 2007-12-24
Hello,

Why is apt-get wanting to upgrade things that don't need upgrading? Specifically, in this case these are the mythtv components and Netatalk. 

Netatalk is sort of understandable since I installed it with SSL support via sources fetched via apt-get, but I'm not sure why it wants to reinstall MythTV.

Is there anyway to register these packages so that apt-get doesn't bother trying to reinstall them via an "apt-get upgrade"? In the case of Netatalk where some manual install attention is needed, this is a pain.

Thanks in advance!

---

### Post by ~LoKe on 2007-12-24
It'll try to update it with the packages found in the repositories.  If they don't match, it'll update.

You can lock packages by opening up synaptic and search for the package.  Right click and lock it.

---

### Post by JimmyHopkins on 2007-12-24
Sorry for lurking but damn ~loke, you're on the ball.

---

### Post by besson3c on 2007-12-24
> **~LoKe said:**
> It'll try to update it with the packages found in the repositories.  If they don't match, it'll update.

You can lock packages by opening up synaptic and search for the package.  Right click and lock it.

So if there are any changes made to the files that were installed it will offer to update them again? Will locking a package lock it indefinitely, or simply until the next version?

---

### Post by forestpixie on 2007-12-24
it locks them until you unlock them again

---

### Post by ~LoKe on 2007-12-24
> **forestpixie said:**
> it locks them until you unlock them again

Correct.  All you have to do if you decide to update them officially is open up synaptic again and unlock the package.  It will remain locked until you manually unlock it.  I believe you can filter by locked packages too, so if there are more you want to lock, feel free to do so, you won't have to hunt them down later.

---

### Post by forestpixie on 2007-12-24
I have openoffice locked at the oo version - they show in a 'pinned' section in status so you don't even need to search :)

---

### Post by besson3c on 2007-12-24
Something must be wrong... I went into Synaptic and locked Netatalk by going to the Package menu -> Lock version. This part seemed to work just fine - the package is red/marked as being locked. However, Netatalk is still coming up as an upgrade option in Gutsy.

Are there any known issues with locking packages?

---

