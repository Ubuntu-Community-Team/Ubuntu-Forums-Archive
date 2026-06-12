---
title: "NTFS-3G uses 100% CPU"
date: 2008-02-13
forum: General Help
---

### Post by nemilar on 2008-02-13
Hey all,

I've been having this problem since day-one: the NTFS-3G driver uses 100% of my CPU when writing to my external drive (SATA connected via USB 2.0).  Reading doesn't use 100%, but it uses far more than it ought to (for example, video playback will use ~40%).  When I look at it in top, it is always the 'mount.ntfs' process eating up my CPU.

I've went through the checklist on the NTFS-3G site here:
[http://www.ntfs-3g.org/support.html#cpu100](http://www.ntfs-3g.org/support.html#cpu100)

And I can't pin down the problem.  I've also search on their forums, but to no avail. I know that the drive is not fragmented, because it was a fresh-format and I've plugged it into a Windows machine to check.

This seems to be a problem many people are having with the NTFS-3G driver, so I was hoping someone here might know of a solution that worked in their situation, or has heard of something working for someone else.

Any help is GREATLY appreciated!

Thanks in advance,
Nemmy

---

### Post by marufaberlin on 2008-02-14
You might try to re*nice* the mount.ntfs program. If it runs with less priority, it might not consume as much CPU. Installing htop, it provides a nice TUI (Text-based UI, ncurses) that also has a *nice* (no pun intended :lolflag:) interface.

---

