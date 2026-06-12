---
title: "NTFS Partition claims to be mounted but isn't"
date: 2007-08-24
forum: General Help
---

### Post by Spaceomega on 2007-08-24
I've been trying to mount my NTFS so I can read/write to it and when I try to mount it to /windows or /media/windows it claims to already be mounted.  I've tried to umount each of those and it doesn't report anything back in the terminal.

Any help?

EDIT:  Alright, got it mounted to /media/windows but NTFS config doesn't seem to be detecting it, seeing as how it isn't writable.  I don't see this screen:

[IMG]http://www.ubuntugeek.com/images/ntfs/2.png[/IMG]
[taken from [here]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")]

EDIT2:  Fixed it.  I just installed the latest NTFS config from their site, then booted into windows and shutdown cleanly and booted back into Ubuntu.

---

