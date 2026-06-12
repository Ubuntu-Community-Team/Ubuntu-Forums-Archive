---
title: "Ubuntu on dual boot machine not booting"
date: 2015-03-18
forum: General Help
---

### Post by pgib8 on 2015-03-18
I think I found a solution to the issue posted in this thread: [http://ubuntuforums.org/showthread.php?t=1925468](http://ubuntuforums.org/showthread.php?t=1925468)

For some reason the thread was closed without an answer, so I couldn't post it there. Maybe somebody wants to add the answer to it and then remove this thread. Keep in mind that these threads aren't always about current discussions but that when people search for solutions, even years later, they may stumble upon them.

Anyway, I had the exact same error message, which was "[COLOR=#000000][FONT=Ubuntu Mono]can't open /proc/self/fd/9[/FONT][/COLOR]" and the system did not boot. All I had to do to fix it was to create the /proc folder, and that was it.
The reason it wasn't there is that when copying a root file system from one folder to the next, some have suggested to --exclude=/proc. Apparently that is wrong and it needs to be copied as well. As [COLOR=#DD4814][COLOR=#000000][linuxpingu]("http://ubuntuforums.org/member.php?u=799892")[/COLOR][/COLOR] also showed their / contents, proc also wasn't shown. Thus I believe this to be the solution.

---

