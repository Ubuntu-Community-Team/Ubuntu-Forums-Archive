---
title: "Totem GStreamer slow playback"
date: 2005-07-05
forum: General Help
---

### Post by DancingSun on 2005-07-05
I'm new to Linux and I'm currently on Ubuntu for AMD64, but I'm wondering if anyone is having similar problems.

In Totem with GStreamer backend, all my video files (xvid, mpeg4, mpg) have slow playback.  Frames are consistently dropped throughout the playback.  Audio is not affected.

When I installed GXine, playback is smooth as it should be.  This leads me to believe that the slow playback is GStreamer related.  I'm wondering if anybody else is having this problem.

---

### Post by steppenwulf241 on 2005-07-05
I had this issue too!

Unfortunately, the only way I was ever able to 'fix' the issue was to uninstall Totem, and replace it with totem-xine...

---

### Post by manicka on 2005-07-05
Yes, totem-xine will fix your problems

---

### Post by DancingSun on 2005-07-05
Ok, so this sounds like a problem with GStreamer.

Assuming that it's true...this might be a big problem...I think GStreamer is suppose to be the default multimedia framework for Ubuntu, right?  I read somewhere that GStreamer handles the preview of sound clips.  I'm assuming that also means the preview of video clips are also handled by GStreamer.

Not good...

Let me do a search on bugzilla...

---

### Post by DancingSun on 2005-07-05
Ok, I found the bug:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11536](https://bugzilla.ubuntu.com/show_bug.cgi?id=11536)

The bug's status is under "NEEDINFO", so If you are having this problem, please add a comment to the bug and provide with further information reguarding the bug. If you don't do this we might be stuck with crappy default performance!

---

