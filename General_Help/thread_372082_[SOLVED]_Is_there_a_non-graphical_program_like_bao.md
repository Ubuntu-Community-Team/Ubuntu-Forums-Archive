---
title: "[SOLVED] Is there a non-graphical program like baobab?"
date: 2007-02-27
forum: General Help
---

### Post by TheApe on 2007-02-27
Hi!
I have a client who has a dedicated host with Free BSD. As I can only login there by ssh and they are complaining about disk quota exceeding, I'd like to know if there is a tool like baobab for console mode. Or some shell script that you've used.

Thank's!! :D

---

### Post by jpeddicord on 2007-02-27
The command you are looking for is `du`. It is preinstalled on most linux+bsd systems using GNU coreutils. Try `man du` for help using it, and for some examples. There are much too many options to list here.

One tip, however, not in the man page, is sorting the results. After your du command, add "| sort" to automatically sort the results by size.

---

### Post by TheApe on 2007-03-01
Thanks, jaco.
I'll give it a try.
I already knew du. But didn't know that I could combine it with the sort command.
By the way, I've found in Baobab the possibility of scanning remote file systems. FTP, or anything else.

[]'s

---

