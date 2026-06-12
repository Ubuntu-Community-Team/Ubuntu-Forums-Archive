---
title: "Lockups in X session, sth to do with stuck pageflips?"
date: 2015-04-03
forum: General Help
---

### Post by lardypies on 2015-04-03
Hi,

I'm having trouble with my X session locking up apparently at random. Everything stops responding except the mouse pointer. I can exit to a tty, but the screen goes blank for around 60s before anything appears. When it finally does I get the see the following error:

kernel: [ **some number**] [drm:intel_pipe_set_base] *ERROR* pipe is still busy with an old pageflip

From there I have tried killing recent processes, but to no avail. When I switch back to the x-session there is the same ~60s delay before anything comes up and again every time I go back to tty. I can restart the session with a ctrl-alt-backspace, not ideal since it seems like it could be recoverable.

Closest thing to my problem that I've found is this post 
[https://bugs.freedesktop.org/show_bug.cgi?id=82612](https://bugs.freedesktop.org/show_bug.cgi?id=82612)
but I wanted to make sure it's the right thing before randomly updating my kernel or intel drivers.

Lenovo X1 Carbon, Ubuntu 14.04 LTS x86_64, some standard intel graphics chip, running with the laptop's screen + an external screen off the mini-dp. 

Glad to provide more info if needed.

James

---

### Post by tgalati4 on 2015-04-03
Add more shared RAM in the BIOS for video.  Sometimes lack of video RAM will cause problems.  Look in /var/log/Xorg.0.log and ~/.xsession-errors for clues.

---

