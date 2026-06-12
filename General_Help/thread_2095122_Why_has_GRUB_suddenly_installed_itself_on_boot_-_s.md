---
title: "Why has GRUB suddenly installed itself on boot - startup?"
date: 2012-12-15
forum: General Help
---

### Post by listerdl on 2012-12-15
I only have one OS on the drive so why is GRUB suddently appearing.

Am I correct in thinking that everytime you update the kernel GRUB is installed?

Thanks

---

### Post by listerdl on 2012-12-15
Yeah think Im just being a dumb-*** here - 

Answer is yes.

(Been a long time since i was using ubuntu)

---

### Post by oldfred on 2012-12-16
Grub updates menu on every kernel update, but does not normally reinstall.

But I saw in the last day or two a update to grub. Did not pay attention to details but it probably reset everything.

---

### Post by Bucky Ball on 2012-12-16
Please mark as solved when satisfied it is. ;)

---

### Post by elmuchacho on 2012-12-16
I believe you stopped the OS badly once, so like Windows does in this situation by showing a menu asking is you want to boot in safe mode, you get this menu with the choice of OS/mode you want to boot with. It's just not as clear, and it happens all the time afterwards.

I solved it by deleting /boot/grub/grubenv

See [http://ubuntuforums.org/showthread.php?t=2089601](http://ubuntuforums.org/showthread.php?t=2089601)

---

### Post by listerdl on 2012-12-22
> **elmuchacho said:**
> I believe you stopped the OS badly once, so like Windows does in this situation by showing a menu asking is you want to boot in safe mode, you get this menu with the choice of OS/mode you want to boot with. It's just not as clear, and it happens all the time afterwards.

I solved it by deleting /boot/grub/grubenv

See [http://ubuntuforums.org/showthread.php?t=2089601](http://ubuntuforums.org/showthread.php?t=2089601)

Yes thanks for all replies. If never came back so I think that is what must have happened - i.e. a bad shutdownn.

I shouldnt bother to delete as you suggest should I?

---

### Post by oldfred on 2012-12-22
If it is now working then there should not be anything to delete. Grub sets that flag on abnormal shutdown as it assumes you may need to use recovery  mode and run fsck or make other fixes.

---

