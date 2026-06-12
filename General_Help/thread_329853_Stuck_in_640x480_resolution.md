---
title: "Stuck in 640x480 resolution"
date: 2007-01-02
forum: General Help
---

### Post by HarrisonHopkins on 2007-01-02
Alright, last night I installed the fglrx drivers for my ATI Radeon Mobility X1400 video card. Everything worked great. I rebooted a few time and I was still in my 1280x800 resolution. I was one happy camper. Howeveer, this morning when I get on, I'm stuck in 640x480 resolution. I figured that it had just got reset to the lowest one, so I go into System Settings->Display. It says that is as the max resolution. What can I do to fix this?

EDIT: Nevermind, I fixed it. I just went and typed 'sudo aticonfig --resolution=0,1280x800,1280x720,800x600,640x480' and then restarted with CTRL-ALT-BACKSPACE.

---

