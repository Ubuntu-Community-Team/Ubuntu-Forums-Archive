---
title: "how to &quot;stopwatch&quot; commands ?"
date: 2007-09-28
forum: General Help
---

### Post by atarianer on 2007-09-28
I'm looking for a command that outputs the duration another command needs to finish...
like
>:/ "stopwatch" updatedb (e.g.)

---

### Post by mcduck on 2007-09-28
The 'time' command is what you are looking for.

For example. 'sudo time updatedb'

It will tell you the time it takes for the command to complete, as well as information about resources used.

See 'man time' for more details.

---

### Post by mcduck on 2007-09-28
* double post..

---

### Post by atarianer on 2007-09-28
thx, thats what i was looking for :)
Thought "time" was just for setting time and stuff ...

---

