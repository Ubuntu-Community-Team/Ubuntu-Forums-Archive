---
title: "[SOLVED] nautilus hanging, no user access to home directory"
date: 2008-02-11
forum: General Help
---

### Post by Riverine on 2008-02-11
Nautilus hangs when I try to access my home directory as the regular user.  The initial display of the directory is normal but there is no response to mouse events, the window fails to close, and reopens if forced close.  If I kill nautilus via the system monitor it restarts, opens the home directory window and hangs again.  Processor utilization for Nautilus pegs at 49% (all of one of two processors) so I'm guessing the code is stuck in a loop.  Unfortunately it is allocating memory while in that loop so eventually this system becomes unresponsive and then crashes.

If I start nautilus as root it seems to work fine.

I have tried booting into an eariler version of the kernel (2.6.22-13) but the problem remained.

Looking around the forums here I can see other people have had this happen to them but I haven't seen any fixes (other than to scratch my user account and create a new one).

Ideas?  Suggestions?

---

### Post by Riverine on 2008-02-11
I'll answer my own post here in case anyone with a similar problem finds this thread.

I looked into nautilus bug reports on Launchpad and found 
[https://bugs.launchpad.net/ubuntu/gutsy/+source/nautilus/+bug/150471]("https://bugs.launchpad.net/ubuntu/gutsy/+source/nautilus/+bug/150471")

Within that bug report one person mentioned that the problem occurred for him due to a corrupt image thumbnail file.  I had just saved a new SVG image when the problem occurred for me so I deleted the .thumbnails directory from my home directory and the problem is (at least for now) solved.

---

