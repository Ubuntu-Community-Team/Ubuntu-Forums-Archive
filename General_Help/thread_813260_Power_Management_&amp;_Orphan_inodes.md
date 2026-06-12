---
title: "Power Management &amp; Orphan inodes"
date: 2008-05-30
forum: General Help
---

### Post by tebbens on 2008-05-30
Ubuntu didn't shutdown fast enough when the UPS was at a critically low level.

Power Manager only offers ...

When UPS power is low: [shutdown/suspend options]
When UPS power is critically low: [shutdown/suspend options]

It doesn't show, or allow you to change the low or critically low level.
Can I change those settings ??


After the HARD shutdown I got the following;

May 30 16:08:00 tebbens-desktop kernel: [   70.039918] EXT3-fs: sda1: orphan cleanup on readonly fs
May 30 16:08:00 tebbens-desktop kernel: [   70.175206] EXT3-fs: sda1: 35 orphan inodes deleted
May 30 16:08:00 tebbens-desktop kernel: [   70.175208] EXT3-fs: recovery complete.
May 30 16:08:00 tebbens-desktop kernel: [   70.374633] EXT3-fs: mounted filesystem with ordered data mode.

How bad are orphan inodes ???

Thanks!

---

