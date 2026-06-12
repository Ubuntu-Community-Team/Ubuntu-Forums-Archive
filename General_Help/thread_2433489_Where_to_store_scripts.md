---
title: "Where to store scripts?"
date: 2019-12-19
forum: General Help
---

### Post by GhX6GZMB on 2019-12-19
Until now I've stored scripts (self-made) in /home, but I wonder if this is the correct place.
The scripts are for all users and are things like screen capture, file conversion and so on.

Would it be more correct to have these in /bin ?

Thank You.

---

### Post by TheFu on 2019-12-19
Personal preference,

Personal scripts, I put into ~/bin/ == same as $HOME/bin/
System scripts for anyone, I put into /usr/local/bin/
Root only scripts, I put into /root/bin/

Be consistent across all systems. That's the most important thing.  Also, following the *File System Hierarchy Standards* doesn't hurt. Really smart people came up with those and thought through pretty much any needs already.  Follow the standards when possible.

Backups need to include all these places.

---

### Post by Tadaen_Sylvermane on 2019-12-19
i haven't got a need to keep my scripts too privately as a home user. as such i have them on my snapraid pool with symlinks into /usr/local/bin. this way all users can use as needed but i maintain them in my normal snapraid syncs. this also prevents me from having to worry about blasting my root partition and losing something not easily replaceable. have spent far to much time on my scripts to get them just right for my use. symlinks are my lifestyle practically.

---

### Post by Skaperen on 2019-12-19
i've put things for "all users" in [COLOR=#0000cd][FONT=courier new]**/usr/local/bin**[/FONT][/COLOR] until recently.  because many packages now put stuff there and because i built a system to refresh my "all users" the needs to delete stuff it doesn't recognize, i created a totally new place to put things in called [COLOR=#0000cd][FONT=courier new]**/usr/host/bin**[/FONT][/COLOR].  [COLOR=#0000cd][FONT=courier new]**ls -1 /usr/host/bin|wc -l**[/FONT][/COLOR] tells me there are 629 commands in there, right now.  many are symlinks for aliasing (they point in the same directory or one of the other standard ones).  lots of my stuff is done in Python3, now, but lots are still in bash or compiled from C.

---

### Post by yetimon_64 on 2019-12-19
> **TheFu said:**
> Personal preference,

Personal scripts, I put into ~/bin/ == same as $HOME/bin/
System scripts for anyone, I put into /usr/local/bin/
Root only scripts, I put into /root/bin/

Be consistent across all systems. That's the most important thing.

Backups need to include all these places.

@ OP, this post from TheFu gets a big "+1" from me. Good sound advice in my opinion.

Regards, yeti.

---

### Post by VMC on 2019-12-20
I think traditionally user scripts belong in "/home/bin" as TheFu stated above.

---

### Post by GhX6GZMB on 2019-12-20
Thank You all.
I'll use /usr/local/bin for the scripts in question (used by all users).

---

