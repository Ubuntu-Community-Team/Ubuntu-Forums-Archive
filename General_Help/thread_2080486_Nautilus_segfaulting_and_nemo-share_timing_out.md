---
title: "Nautilus segfaulting and nemo-share timing out"
date: 2012-11-04
forum: General Help
---

### Post by lordzanny on 2012-11-04
After doing a fresh 12.10 install on an A10-5800k media center pc, Nautilus started segfaulting after a reboot whenever it was started (often it wouldn't even show anything).  A GDB said it was happening in vfprintf in libc.  I attempted reinstalling it, deleting preferences under ~/.config/nautilus, and even tried using Nautilus 3.6, but the only work around I found without probably reinstalling the OS was to just use nemo.

And that would have been fine, but now nemo has timeout issues with network shares, which is kind of a big deal with a media pc.  If I try to scan the local SMB network it either times out or runs extremely slowly (even though bandwidth is still 100mbps+).

I tried Marlin, but it doesn't have any integrated SMB support.  So I'm either going to reinstall and hope Nautilus doesn't start segfaulting, or get Nemo samba shares working somehow.  After an hour of googling, this doesn't seem to be a problem for anyone in recent times.  Both of these work just fine off my live usb too ( samba shares and nautilus).

TLDR: Nautilus segfaults on start even with wiped local configuration, and Samba network scanning times out or runs extremely slowly on Nemo.

---

