---
title: "schroot?"
date: 2007-07-10
forum: General Help
---

### Post by Hendrixski on 2007-07-10
I want to have a chroot for development, so that I don't clutter up my base system with dev packages, and so that I don't bork anything in the base system from tinkering.  I've used dchroot, and there's a bit of documentation about this but I've heard a few times that schroot is better, that I should be using schroot.

I've tried several times to port over to schroot but always found that there just isn't any good documentation about it.  Good documentation is a key requirement for a development tool, so I was wondering if anyone here uses schroot, and if it's good enough for use developing?

If anyone has any helpful links, or can tell me how to install an schroot, then please do so on this thread.  The man page is great, but doesn't have anything about how to set up a new one or how to debootstrap a system into one!

---

### Post by rleigh-debian on 2008-07-05
You just need to

1) Run debootstrap to create a new chroot in a directory of your choosing.  The manual page for debootstrap should be sufficient to make this work, plus the URI for a Debian or Ubuntu mirror.
2) Edit /etc/schroot/schroot.conf to let schroot know about it (I recommend the "directory" type for the simple case).

If you have any questions or problems with schroot, the mailing list is the best place to ask (buildd-tools-devel at lists.alioth.debian.org)


Regards,
Roger

---

