---
title: "Opera dumpes core w/ ATI flgrx driver [SOLVED]"
date: 2007-10-24
forum: General Help
---

### Post by kristianz on 2007-10-24
I don't actually need help, I'm just posting this in case others are experiencing the same problem and cannot find a solution.

Issue: Opera won't start, exits at start-up with "Floating point exception (core dumped)".

Solution: In the Device-section of xorg.conf,
change this:
  Option      "VideoOverlay" "on"
to this:
  Option            "TexturedVideo" "on"

Hope this helps someone. I did get this problem right away with a fresh Ubuntu 7.04 install, and I was so disappointed that Opera wouldn't work (Firefox is a nightmare to work with when you're used to Opera). I eventually got it working by mucking about with the xorg.conf file, but had other issues as a result. I recently fixed my xorg to solve those issues, but then Opera wouldn't work. So I found the culprit line in xorg.conf by trial-and-error.

---

