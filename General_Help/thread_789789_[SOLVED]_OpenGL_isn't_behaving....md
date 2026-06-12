---
title: "[SOLVED] OpenGL isn't behaving..."
date: 2008-05-10
forum: General Help
---

### Post by ByKeLaO on 2008-05-10
I've just done a fresh install of Ubuntu Hardy, and I'm already having problems :(
The first thing I did was to install the nvidia-glx-new package and the nvidia driver, then install all of the updates.
I then installed Ogre 3D and netbeans so I could dabble in 3D programming.
I compiled the samples that came with Ogre 3D, but they all refused to run, just producing a blank screen every time.
I thought it was just a problem with Ogre 3D, but it seems to be the same with every openGL program I run. And none of these programs report any errors.
How can I fix this?

EDIT: Compiz fusion is disabled, in case that's important ;)

---

### Post by ByKeLaO on 2008-05-10
These entries appear in my kern.log after running the Ogre 3D sample apps, I dunno if this is relevant or not:

May 11 03:51:47 james-desktop kernel: [ 2125.962274] NVRM: Xid (0001:00): 13, 0002 beef3097 00004097 00000208 0000012b 00000002
May 11 03:51:47 james-desktop kernel: [ 2125.962809] NVRM: Xid (0001:00): 36,  L0 -> L0
May 11 04:02:25 james-desktop kernel: [ 2762.434260] NVRM: Xid (0001:00): 13, 0002 beef3097 00004097 00000208 0000012b 00000002
May 11 04:02:25 james-desktop kernel: [ 2762.434791] NVRM: Xid (0001:00): 36,  L0 -> L0
May 11 04:06:04 james-desktop kernel: [ 2981.372035] NVRM: Xid (0001:00): 13, 0002 beef3097 00004097 00000208 0000012b 00000002
May 11 04:06:04 james-desktop kernel: [ 2981.372568] NVRM: Xid (0001:00): 36,  L0 -> L0
May 11 04:06:17 james-desktop kernel: [ 2994.866335] NVRM: Xid (0001:00): 13, 0002 beef3097 00004097 00000208 0000012b 00000002
May 11 04:06:17 james-desktop kernel: [ 2994.866878] NVRM: Xid (0001:00): 36,  L0 -> L0
May 11 04:07:54 james-desktop kernel: [ 3091.762033] NVRM: Xid (0001:00): 13, 0002 beef3097 00004097 00000208 0000012b 00000002
May 11 04:07:54 james-desktop kernel: [ 3091.762568] NVRM: Xid (0001:00): 36,  L0 -> L0

---

### Post by ByKeLaO on 2008-05-24
Not sure if this helps anyone, but I found a workaround. Apparently this is a bug in the current release of Ogre and should be properly fixed soon.
Until then, set the RTT Preferred mode to PBuffer.

---

