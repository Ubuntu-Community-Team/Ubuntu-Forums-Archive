---
title: "Create e2fsck output on autocheck"
date: 2012-11-01
forum: General Help
---

### Post by uriel1998 on 2012-11-01
As intended, e2fsck runs automagically every 30-odd boots on my system.  I have no problem with that... but I'm impatient.  I want a progress bar or some kind of output when it runs on boot.  (I often hit ESC when it's running.)

Looking through the man page, I see this:

**-C**   This option causes **e2fsck**  to write completion information to the specified file descriptor  so that the progress of the filesystem  check can be monitored.  This option is typically used by programs  which are running **e2fsck**.  If the file descriptor specified is 0,  **e2fsck**  will print a completion bar as it goes about its business.  This requires that e2fsck is running on a video console or terminal. So it seems like I should have it running 

```
e2fsck -C 0
```Which looks ideal, but I don't know where the e2fsck command is being triggered from to alter it.  (Every time I've poked at startup commands without knowing exactly what I'm doing I've ended up borking my system, so I'm kind of leery of just altering stuff willy-nilly.)

So my questions are these:

1. Is the command I quoted above going to give me the desired behavior?
2. Where is command being run from so that I can change it? (I'm running 10.04 still, but I imagine this is still something unchanged.)

Thanks in advance!

---

