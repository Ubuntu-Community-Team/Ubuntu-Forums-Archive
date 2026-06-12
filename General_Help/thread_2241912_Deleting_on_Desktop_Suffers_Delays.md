---
title: "Deleting on Desktop Suffers Delays"
date: 2014-08-29
forum: General Help
---

### Post by texpat on 2014-08-29
This is on Xubuntu 14.04

If I select a file or directory on the desktop and want to dump it into the trash bin using the [DELETE] key, the operation will take like 15-20 seconds to complete and it won't let me do anything else on the desktop (I can still use other windows, though).

This doesn't happen if I click-drag the icons into the bin. In a terminal [FONT=Courier New]**mv**[/FONT] or [FONT=Courier New]**rm**[/FONT] work instantly.

Ideas? Solutions?

Thanks for reading :-)
Tx

---

### Post by Elfy on 2014-08-29
There was a bug I found during trusty testing which got a fix, seems the fix was reverted.

Not sure what's going to happen now - will report back once I find out, in the meantime you can me too the current bug 

[https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1319029/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+source/xfdesktop4/+bug/1319029/+affectsmetoo)

[https://bugzilla.xfce.org/show_bug.cgi?id=10778](https://bugzilla.xfce.org/show_bug.cgi?id=10778)

---

