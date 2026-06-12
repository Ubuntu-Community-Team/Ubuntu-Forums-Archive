---
title: "How to prevent app &quot;no response&quot; dialog from popping up?"
date: 2018-03-07
forum: General Help
---

### Post by myocytebd2 on 2018-03-07
How to prevent app "no response" dialog from popping up?

I have some UI programs that runs very slow (e.g. software being tested under valgrind).
The app "no response" dialog pops up from time to time, giving me a lot of trouble 
(e.g. the dialog grabs input; and occasionally break testing, as the event loop stalls until I manually focus it).

---

### Post by tinylagarto on 2018-03-07
I saw something like this when my system was under heavy load. How much RAM do you have?

---

### Post by myocytebd2 on 2018-03-07
In my case, it is slow because I run programs under valgrind (software development tool for memory related checking) for testing.
So it is very slow as expected, and I cannot control its speed.
But the automatically test running are interfered by the popup dialog, so I really want to get rid of it.

---

