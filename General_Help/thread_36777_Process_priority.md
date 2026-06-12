---
title: "Process priority?"
date: 2005-05-24
forum: General Help
---

### Post by arathorn2nd on 2005-05-24
Hi folks

I just got my laptop up and running with Hoary, and I gotta say, it's awesome. I'm never been a real linux user, just messed with some distros, but this one actually made me forget windows.

Anyway, I'd like to ask if is there a process browser like windows Task Manager, and if it's possible to set priorities for one given process.
I'm gaming a lot on linux (UT2004/Shogo/Simcity3k), and most games use up all free resources. I'd like to set some programs running on background to a higher priority so they wouldn't be slowed down by the games.

Any ideas?

Cheers.

---

### Post by JonahRowley on 2005-05-24
**top** can do this, and so can the **renice** command.  I do this all the time, it's very useful on slower machines.

---

### Post by arathorn2nd on 2005-05-24
[QUOTE=JonahRowley]**top** can do this, and so can the **renice** command.  I do this all the time, it's very useful on slower machines.[/QUOTE]
Exactly what I've been looking for.
One last question: Renice changes the priority to +X or -X
But I don't know what means a higher priority.
I see some processes like reiserfs with priorities like -10.
Does that means the process has a higher priority over the rest?

Forget it, just found out. Less is more in this case :D

---

