---
title: "Conky only runs with Sudo?"
date: 2007-11-30
forum: General Help
---

### Post by quoderat on 2007-11-30
Running Gutsy Gibbon X64, and installed Conky from the repos.

However, it will only run with sudo, and not as my user.

This is the error I get at the terminal when I run it as myself:

conky: timed_thread.c:153: timed_thread_test: Assertion `p_timed_thread != ((void *)0)' failed.

However, when sudoed, it runs fine.

Any ideas on how to fix? Looks like a great program.

---

### Post by logos34 on 2007-11-30
is .conkyrc file in home dir or somewhere else (like /etc?)

---

### Post by quoderat on 2007-11-30
Thanks for replying. No, .conkyrc file is in my home directory.

Strangely, even though I haven't changed anything at all, I just started Conky again, and it ran fine.

That, I can't explain.

---

### Post by quoderat on 2007-11-30
Hmm, actually, I tried to start it again and got the same error message, and it again failed to start.

I tried to start it many more times, and it seems like it manages to start maybe one out of six or seven tries.

Very odd.

So, basically, it's not working. It's not running as a process or anything when I attempt to start it.

---

