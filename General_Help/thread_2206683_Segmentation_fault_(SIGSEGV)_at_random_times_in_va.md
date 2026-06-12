---
title: "Segmentation fault (SIGSEGV) at random times in various programs"
date: 2014-02-20
forum: General Help
---

### Post by 9-me-1 on 2014-02-20
Hi all,

I have the following problem - since getting a new laptop, I keep getting Segmentation Fault (SIGSEGV) many times a day. It seems to happen to all programs, with frequency correlating with how much RAM they use. (So, most often firefox and IntelliJ IDEA).

Can any of you ubuntu experts help me find the root cause? Are there any logs or system commands I could use to discover more about the problem?

Ah yes, I'm running Gnome with i3 as the window manager, and will be happy to provide further info if that helps diagnose the problem.

---

### Post by lukeiamyourfather on 2014-02-20
It sounds like a hardware issue, perhaps a faulty memory module. There are various utilities to run a memory check. If I'm not mistaken there's one on the live Ubuntu installer.

---

### Post by 9-me-1 on 2014-02-25
Right you are. I ran memtest86, and it turns out one of the memory modules was defective. Thanks!

---

### Post by lukeiamyourfather on 2014-02-25
I'm glad you found the culprit! For anyone else who comes across this in the future when searching or whatever, the tell-tale sign was the statement about ***everything*** crashing and not just one application.

---

