---
title: "Ubuntu Gutsy suddenly hanging."
date: 2007-12-11
forum: General Help
---

### Post by gustavo :) on 2007-12-11
Hello, I have a problem here that I don't know how to solve.
The system just suddenly HANGS, without reason. It's happened I was watching a video on youtube, when I opened Deluge to download a torrent, when I was listening music on Exaile, so it isn't exact.
I just can't move anything, the mouse, keyboard, everything hangs so I have to reset and there's no information about the problem, then.
What can I do?

---

### Post by dcstar on 2007-12-11
> **gustavo :) said:**
> Hello, I have a problem here that I don't know how to solve.
The system just suddenly HANGS, without reason. It's happened I was watching a video on youtube, when I opened Deluge to download a torrent, when I was listening music on Exaile, so it isn't exact.
I just can't move anything, the mouse, keyboard, everything hangs so I have to reset and there's no information about the problem, then.
What can I do?

Boot up and run the memtest option in the Grub menu, let it run for a couple of hours to test the reliability of your hardware.

Then boot of an Ubuntu Live CD and see if the system runs more reliably.

---

### Post by ewr2san on 2007-12-12
Also take a look at the /var/log/messages around the time of the crash.  Hopefully it logged something that would give a clue.

---

### Post by emil.s on 2007-12-16
Try to only download some torrent, and don't do anything else. You may have the same problem as i have, and many others:
[https://bugs.launchpad.net/ubuntu/+bug/158037](https://bugs.launchpad.net/ubuntu/+bug/158037)

---

