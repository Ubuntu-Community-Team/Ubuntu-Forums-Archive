---
title: "Booting custom kernels with UUID"
date: 2006-12-17
forum: General Help
---

### Post by Cyber Dog on 2006-12-17
I've been using custom linux kernels from the stock source at kernel.org under Debian for some time now. This week I decided to make a run at an Ubuntu minimal install instead.  Almost everything is working, but with one problem: I can't boot my kernels because of the root=UUID=xxx entries in grub.

I'm using reiserfs filesystems.  As a test, I tried booting the generic kernel, and it does in fact boot normally (or at least at all).  My custom kernels, on the other hand, cause a kernel panic at boot (vfs can't find root fs).  Interestingly if I change the grub menu.lst by simply removing the root=UUID=xxx text, my kernel boots just fine.  

This all leads me to believe that there is some option in the generic kernel that is built in which allows it to support these UUIDs.  Unfortunately, I haven't had much success finding out what feature this might be.  What needs to be enabled to boot a non-Ubuntu kernel using UUIDs?

One other note, I'm not using initrd images.

Thanks-

---

