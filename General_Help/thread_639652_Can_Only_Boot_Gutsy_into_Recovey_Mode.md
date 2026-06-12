---
title: "Can Only Boot Gutsy into Recovey Mode"
date: 2007-12-13
forum: General Help
---

### Post by earthdragon on 2007-12-13
When I turn on my computer it hangs at the Ubuntu loading screen. I can boot into recovery mode, and its trivial to just type init 3 to get into gdm, but it is annoying and not very good when you are showing off Ubuntu. This problem occurs on both my mother laptop (which is a 32 bit machine) and my desktop (which is a 64bit machine running the 64bit version of Ubuntu). Is there something I need to disable to allow Ubuntu to boot regularly?

---

### Post by mocoloco on 2007-12-13
Try disabling the splash screen.  When grub loads, hit "e" for edit mode, then "e" again to edit the line of text.  Remove the word "splash" from the line and hit enter, then I think it's "b" for boot or something like that, it will tell you on the screen.  Even if the splash screen isn't the cause of the problem, with it disabled you should be able to see system messages that might help determine what the issue is.

---

