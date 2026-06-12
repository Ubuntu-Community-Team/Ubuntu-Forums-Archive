---
title: "Kernel Update Notifications"
date: 2021-05-20
forum: General Help
---

### Post by Quarkrad on 2021-05-20
Running 20.04.  On one of my machines I had trouble with boot and shutdown that I finally resolved by using kernel 5.4.  During the process of sorting it all out I installed Mainline/UKuu (Ubuntu Kernel update utility) that is now fully removed.  Having configured grub so that I now boot, by default, to 5.4 I keep getting notifications (that I've never had) of new kernels available (see attached).  How can I get rid of this notification?  (This is my wife's machine - she finds it annoying and asked me to stop it).  Also, I keep reading that it is not advisable not to upgrade the kernel (for all sorts of reasons including security) but many kernel updates from 5.4 give me problems either booting or shutting down.

---

### Post by mikewhatever on 2021-05-20
Apparently, the repository is still there. You can remove it with Software&Updates -> Other Software tab.

I prefer a stable, well tested and actively supported kerel, such as 5.4. The only reason to use a newer one is better support for newer hardware.
I use very old machines, so 5.4 or older is the default choice.

---

