---
title: "how do i edit grub's menu.lst from busybox"
date: 2006-12-30
forum: General Help
---

### Post by col.panic on 2006-12-30
](*,) so i can't boot ubuntu right now it is trying to boot sda1 instead of hda1.  I can't edit it on boot from within grub because the drivers for my keyboard are loaded after grub is(long story don't ask).  I can't boot from anything but a floppy disk drive(external and i no longer have one) or the internal hd.  So once it tries looking for sda1 for the root filesystem it drops to a very basic busybox shell I am able to mount hda1 and view the files on it but i can't figure out how to edit them.  Normally i would use vi or nano but those are not built into the busybox environment.  Any ideas?

---

### Post by ~LoKe on 2006-12-30
Just boot up the Ubuntu LiveCD?

**EDIT:** try busybox-vi as an editor.

---

### Post by col.panic on 2006-12-30
i'll try busybox-vi i assume that is the command... i didn't see it when i typed help but will try.... The live cd is out of the question because a) don't have one and don't have the means to get one(too big a dl) and b) don't have a cd rom drive and c) can't boot from cd

---

### Post by col.panic on 2006-12-30
no unfortunately vi doesn't work....:-k

---

