---
title: "inotifywait stopped working after yesterday update."
date: 2013-01-19
forum: General Help
---

### Post by ibbles on 2013-01-19
I got rather extensive bunch of updates from Muon update manager yesterday, among them a new Linux image, and since then inotifywait have stopped working. The error message, listed in full below, hints that the kernel has been compiled with a different configuration compared to the last kernel I had.

Is inotifywait not supported anymore? Can I install something that will fix it? What should I use instead? Must I get a kernel image from somewhere else?


The error message:
```

$inotifywait someFile.txt
Couldn't initialize inotify.  Are you running Linux 2.6.13 or later, and was the
CONFIG_INOTIFY option enabled when your kernel was compiled?  If so, 
something mysterious has gone wrong.  Please e-mail radu.voicilas@gmail.com
 and mention that you saw this message.

```

I have not mailed radu.voicilas yet.


Some system info:
```

$uname -a
Linux meno 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by natewiebe13 on 2013-01-30
AFAIK the issue is the 3.5.0-22 kernel. Revert to an older one for now to fix the issue.

---

### Post by adusty on 2013-01-31
I've the same problem, later I'll try to reboot with an older kernel.

In the meantime does anyone knows if there is an open bug report for the problem?

---

### Post by sean4u on 2013-01-31
I have this problem on Ubuntu 12.04 desktop for the last few days too, though inotify-wait works just fine at first for hours in a bash script that runs some applications when a file changes.

uname -a says:
Linux bulldozer 3.2.0-36-generic #57-Ubuntu SMP Tue Jan 8 21:44:52 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

