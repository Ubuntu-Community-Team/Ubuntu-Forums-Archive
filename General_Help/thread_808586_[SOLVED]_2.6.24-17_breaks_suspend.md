---
title: "[SOLVED] 2.6.24-17 breaks suspend"
date: 2008-05-26
forum: General Help
---

### Post by FuturePilot on 2008-05-26
After upgrading to the 2.6.24-17 kernel suspend broke on two of my computers. Both display the same symptoms. After resuming from suspend, the screen never comes back on. It's not just a blank screen, it never powers back on at all. One of these computers is a laptop with a GeForce2 Go and the other is a PC with a GeForce 6600. Suspend worked great on both of these before the update.

Is anyone else having this problem? Any ideas?

---

### Post by 61811 on 2008-05-26
Same problem here too. Updated only one of my three computers, and it broke the Suspend feature. Older kernel -16 still works fine.

Machine: Dell Dimension 4700 with integrated video.

---

### Post by steveneddy on 2008-05-26
I'm on the 64 bit kernel and the 2.6.24-17 kernel and suspend works for me.

edit:

I just tested hibernate and it still works, also.

AFAIK I don't have any special settings in any config files that I know about.

---

### Post by FuturePilot on 2008-05-27
Ah, found the bug. A number of people are having this problem. Same symptoms. Hard drive comes on and that's about it. No screen, no wireless, no nothing. :(

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279")

---

### Post by mivo on 2008-05-27
Thanks for the heads-up. I saw the kernel updates and figured I should wait and check the forums first.

---

### Post by FuturePilot on 2008-06-17
Fixed with the -19 update \\:D/

---

