---
title: "nautilus delayed exit. looking for templates?"
date: 2018-05-28
forum: General Help
---

### Post by drhex on 2018-05-28
Ubuntu 18.04

I'm starting Nautilus from a script.  It starts and works fine. When the user clicks the X in the corner to exit, the window is closed immediately but it takes another 12 seconds before the command finishes.
I've tried to find out why Nautilus takes so long to exit by using strace:

```
strace -t -o /tmp/file nautilus
```

This gives a large file with all the syscalls the program makes along with timestamps.  The delay is due to two calls to poll() taking 7 and 5 seconds respectively.  The filedescriptor polled is connected with inotify_add_watch to the "Templates" folder in the users's home directory (that folder is empty).
I tried removing the Templates folder but that just causes Nautilus to hang on the home directory itself instead.

Any ideas as to what Nautilus expects to find in the Templates directory while exiting or what could be done to speed up the exit?

---

