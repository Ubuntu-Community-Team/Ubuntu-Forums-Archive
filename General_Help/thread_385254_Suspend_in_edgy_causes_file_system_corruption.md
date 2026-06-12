---
title: "Suspend in edgy causes file system corruption"
date: 2007-03-15
forum: General Help
---

### Post by vav on 2007-03-15
My computer (Inspiron 9300, WXGA+ screen, radeon driver(3d works)) suspends in 3-4 seconds... great.
But if I try to wake it up, a blank screen with mouse cursor shows up.
If I then try to do a text login by pressing Ctrl+Alt+F1, it shows me the login screen, but as soon as I enter my username it gives ext3-fs error or some other file system error. I ran fsck manually and it fixed a couple of inodes here and there, but the next time I had the same problem...

Any ideas?

---

### Post by yopnono on 2007-03-15
> **vav said:**
> My computer (Inspiron 9300, WXGA+ screen, radeon driver(3d works)) suspends in 3-4 seconds... great.
But if I try to wake it up, a blank screen with mouse cursor shows up.
If I then try to do a text login by pressing Ctrl+Alt+F1, it shows me the login screen, but as soon as I enter my username it gives ext3-fs error or some other file system error. I ran fsck manually and it fixed a couple of inodes here and there, but the next time I had the same problem...

Any ideas?

Have the same, it sometimes happens after suspend. Then I get file system errors.
Sorry don't know why, have searched but not found any good answer to it, maybe it's time to file a bug.

EDIT:
Using a DELL D610 intel graphic,

---

### Post by yopnono on 2007-03-15
I have filed a bug report for this issue. Add more info to the bug report if you like.

[https://launchpad.net/bugs/92592](https://launchpad.net/bugs/92592)

---

