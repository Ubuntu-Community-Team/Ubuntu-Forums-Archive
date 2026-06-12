---
title: "Read-only device?"
date: 2007-05-03
forum: General Help
---

### Post by Vinze on 2007-05-03
Hey, my brother's got this SD card or whatever it's called, which he put into a USB card reader so that it is detected by Xubuntu as a "2G Removable Volume". However, when I open it, I cannot write to any file, regardless of me being root or not. Apparently it's a read-only filesystem or something, but I want to write to it! How can I do this?

Thanks in advance.

---

### Post by disposable on 2007-05-03
This sounds like the USB bug that plagues Feisty:

[http://ubuntuforums.org/showthread.php?t=431530](http://ubuntuforums.org/showthread.php?t=431530)

pmount is the workaround.

---

### Post by Vinze on 2007-05-04
> **disposable said:**
> This sounds like the USB bug that plagues Feisty:

[http://ubuntuforums.org/showthread.php?t=431530](http://ubuntuforums.org/showthread.php?t=431530)

pmount is the workaround.

Too bad, but pmount didn't solve the problem :(

---

