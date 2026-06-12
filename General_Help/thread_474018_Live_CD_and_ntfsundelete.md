---
title: "Live CD and ntfsundelete"
date: 2007-06-14
forum: General Help
---

### Post by pfunked on 2007-06-14
Thanks in advance to anyone who can point me somewhere.

My roommate's Windows computer is fubar (the OS will have to be reinstalled), and before I reformat it I want to see if I can use ntfsundelete to recover some of the data he's lost.

I can boot the machine from an Ubuntu Live CD.  I can access his ntfs partition through Gnome and peek around it.  The folders which contained the missing data exist but are blank.

I try to run ntfsundelete but I don't know what parameter to use for **device ** (e.g. /dev/hda1).  Where does the Live CD mount a Windows machine's C: drive by default, or specifically what device parameter should I use when running ntfsundelete from a live CD?

(for those wondering, I hope to move any recoverable data to a USB drive).

Of course, if I can't get this to work I'll yank out his drive, slave it on my spare windows machine, and find some windows utilities to do the equivalent.  But it seems this is an opportunity for Ubuntu to shine.

Thanks,
pfunked

---

### Post by jasonlfunk on 2007-06-14
I am not positive, someone else can verify it, but check in /media/. They may be in there.

EDIT: You wanted the device, not the mount point. :) Opps.  Try df, that should tell you.

---

