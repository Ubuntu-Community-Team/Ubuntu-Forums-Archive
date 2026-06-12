---
title: "WINE file locations?"
date: 2007-07-29
forum: General Help
---

### Post by master_runner on 2007-07-29
Mk. so, my question seems pretty simple, but I'm unable to find an answer from manpages or anything. :(

So, let's say I have a file that windows apps see as C:\Program Files\Program.exe
Where would that be in reference to /? that is, where is WINE's C:\ in the Linux file system?

Thanks!

---

### Post by Happy_Man on 2007-07-29
That would be a reference to ~/.wine/drive_c/Program Files/Program.exe.

---

### Post by Old *ix Geek on 2007-07-29
Look in your **.wine** directory to see the full structure; as the other reply said, the files you're talking about will be found in its **drive_c** subdirectory.  But there are other entries, too, which you might want to see just for familiarity.

---

### Post by master_runner on 2007-07-29
I found it, Thanks! :)

---

