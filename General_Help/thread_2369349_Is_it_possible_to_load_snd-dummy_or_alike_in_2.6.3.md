---
title: "Is it possible to load snd-dummy or alike in 2.6.32-042 somehow?"
date: 2017-08-22
forum: General Help
---

### Post by zeppan on 2017-08-22
Hello everyone

I am pretty new to linux and ubuntu overall! I have recently started to play around with Ubuntu 16.04 and VPS and noticed that some vps come forced with an old kernel 2.6.32-042 which somehow won't update

Or atleast i haven't managed... I have also read this is due to openvz running on the host machine.

My main problem with this is that i want to enable the snd-dummy using "sudo modprobe snd-dummy" since some apps require this!

I have yet to find a way to do this. Other solutions which enable a dummy sound output are also welcome! I just need some applications to believe its there.

Any help would be appreciated.. really new to all this!

---

### Post by TheFu on 2017-08-23
You need HVM solutions like Xen or KVM.

openvz uses a paravirtual method. That means 1 kernel is used across all the VMs.  You don't have control over any kernel modules that the base-OS doesn't include either.  This is more efficient for the systems, but removes some control for each guest VM.  Trade-offs.

At least that was how everything worked last time I looked at openvz about 8 yrs ago.

---

