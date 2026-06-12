---
title: "[SOLVED] Switching Screen Configuration (2 screens to 1)"
date: 2008-02-09
forum: General Help
---

### Post by Sam Lars on 2008-02-09
I have my dual-head card set up with two monitors.  Usually I can switch between using them both and using just one.  Now I can't... in nvidia-settings, it tells me this when I try to disable one:

Failed to set MetaMode (1) 'CRT-0: 1280x1024 @1280x1024 +0+0' (Mode 1280x1024, id: 50) on X screen 0.

I've tried a few things, and I don't want to have to log out to change it... it's worked before... any ideas?

---

### Post by Sam Lars on 2008-02-10
Okay, I fixed it by going through dpkg-reconfigure and adding back my specifics... I think I had told nvidia-settings to save the configuration, and it added a bunch of modelines and stuff...

---

