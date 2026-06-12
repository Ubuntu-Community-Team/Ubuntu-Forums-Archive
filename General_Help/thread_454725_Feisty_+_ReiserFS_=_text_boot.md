---
title: "Feisty + ReiserFS = text boot?"
date: 2007-05-25
forum: General Help
---

### Post by larini on 2007-05-25
Hi, I just reinstall my Feisty using reiserfs instead of ext3. i'm happy with reiser, but in middle of the boot, the system goes to text scroll and then goes to X again to login.

Why the boot is going to text screen?

---

### Post by kidders on 2007-05-27
Hi there,

The cause depends on exactly what's happening. For instance, if X is failing to start on its first attempt (which is what you seem to be suggesting), it may be because your input devices aren't ready on time. That might happen if, for example, you're using a bluetooth mouse.

X normally tries to start three times before giving up. In between restarts, you might be left staring at debug output from services that usually start after it, for a few moments.

---

### Post by Klin'Targ on 2007-06-01
This is happening to me as well during journal playback at boot. The journal text is showing up twice on my machine, which may be what is causing the bootsplash to timeout and drop to text mode, thinking a service is taking too long to start.

---

### Post by steeleyuk on 2007-06-01
> Why the boot is going to text screen?

This is normal when using ReiserFS. At boot the journal is replayed to check that the file system is 'clean'.

Wiki article on [journaling]("http://en.wikipedia.org/wiki/Journaling_file_system").

---

### Post by Ptero-4 on 2007-06-20
Actually in my old Mac, I use Reiser and it doesn't cause usplash to timeout at all.

---

