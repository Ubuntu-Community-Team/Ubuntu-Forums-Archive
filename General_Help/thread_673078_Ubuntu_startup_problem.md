---
title: "Ubuntu startup problem"
date: 2008-01-20
forum: General Help
---

### Post by jack_harper2007 on 2008-01-20
Every time i try to start Ubuntu normally it takes a lot of time to get to the log in screen and sometimes it doesn't even get there. It's much faster if i start it with recovery mode and it doesn't give me any problems. Is there a way to speedup Ubuntu startup? And start it normally? I really need it to start normally (not by the recovery mode). Thanks.

I have Ubuntu 7.10

---

### Post by ajgreeny on 2008-01-20
There must be a problem with the boot process.  Next time you boot the machine go to the standard boot line in grub for ubuntu, not recovery, and hit "e" key, then in the screen which appears go to the line starting kernel and use "e" again. Now using the cursor keys go to the end and delete the words "quiet splash" from the end.  Hit enter and then "b" to boot up with all the boot code showing. This should give you a clue where the delay is coming from and we can try to help further from that point.  These changes will not affect your boot at other times, just this once.

---

