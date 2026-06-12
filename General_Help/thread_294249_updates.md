---
title: "updates"
date: 2006-11-06
forum: General Help
---

### Post by tronica on 2006-11-06
I updated my kernel to 2.6.18-1 and the update manager is still saying I have updates for linux-restricted-modules for the old kernel. I went into synaptic and locked my current kernel thinking that may help. Any ideas. also locking my current kernel version wont' give me any problem will it?

---

### Post by mbeierl on 2006-11-06
I take it you compiled and installed your own 2.6.18-1 kernel.

The way the Ubuntu repositories and packages are structured gives you a meta-package (say linux-686.)  To quote its description:

This package will always depend on the latest complete Linux kernel available for Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV.

Which means that the Ubuntu devs can post fixes and as long as you have that package installed, it will "follow" the latest fix version.

In your case, you chose to install a newer version.  The linux-686 package does not know about your version: it continues to follow the "official" version in the repositories.  So, whenever an update is available, you will be notified, even though you may already have a newer version.

This is part of the beauty of Ubuntu: you'll always know where the official release is at, while at the same time you are free to go your own way...

Locking your kernel version won't really hurt anything, as long as you continue to maintain your own kernel.  I think it's better just to leave the default package alone.  That way you'll always have a known working kernel to which to fall back in the event of bleeding edge kernel failure :)

Hope this helps!

---

### Post by tronica on 2006-11-06
Good idea, thanks for the info. I didn't need to upgrade my kernel, but I like having the latest and greatest. Thanks for info.

---

