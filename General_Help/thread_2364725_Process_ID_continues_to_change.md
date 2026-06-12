---
title: "Process ID continues to change"
date: 2017-06-27
forum: General Help
---

### Post by jwhitener on 2017-06-27
```
jason@jason-Meerkat:~$ ps -ef | grep vlc && date
jason    12388 12343  0 01:40 pts/4    00:00:00 grep --color=auto vlc
Tue Jun 27 01:40:12 PDT 2017
jason@jason-Meerkat:~$ ps -ef | grep vlc && date
jason    12394 12343  0 01:40 pts/4    00:00:00 grep --color=auto vlc
Tue Jun 27 01:40:13 PDT 2017
jason@jason-Meerkat:~$ ps -ef | grep vlc && date
jason    12398 12343  0 01:40 pts/4    00:00:00 grep --color=auto vlc
Tue Jun 27 01:40:14 PDT 2017
jason@jason-Meerkat:~$ ps -ef | grep vlc && date
jason    12402 12343  0 01:40 pts/4    00:00:00 grep --color=auto vlc
Tue Jun 27 01:40:15 PDT 2017
jason@jason-Meerkat:~$ 
```

Playing a TV show with VLC, the icon and video disappeared.  I can still hear the sound though.  I want to kill -9 the process, but ever time I try, it says "process not found".  As you can see above, the 'vlc' process keeps changing rapidly.  What is going on here, and how can I kill an ever changing process?

Googling a bit, I found some people saying that there must be a parent process spawning new vlc processes, but none of the suggested commands work to find the parent.  Any ideas?

---

### Post by CatKiller on 2017-06-27
The things you've listed are the process ids for grep. The numbers are changing because you're running grep many times.

---

### Post by jwhitener on 2017-06-27
/smacks own face

Well that was stupid of me.  If any mod wants to delete this waste of space, I'd appreciate it:)

---

### Post by CatKiller on 2017-06-27
It happens to all of us at some point :)

---

### Post by sisco311 on 2017-06-27
I'm still curious which process produces the sound...

We don't delete threads, but if you wish you can use the `report post' button to ask a moderator to move your thread to a non public are.

---

