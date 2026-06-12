---
title: "How to replay a recorded log file in python"
date: 2017-03-22
forum: General Help
---

### Post by vineshv on 2017-03-22
I have recorded a log file log.txt using 'script log.txt' & executed some commands like; date, datetime etc...
Is there any option to replay the log.txt file ?

---

### Post by TheFu on 2017-03-22
scriptreplay?  Is this a trick question?  Ah ... in python. Use the system() command to call "scriptreplay". ;)

From the manpage:

```
REPLAY(1)                        User Commands                       REPLAY(1)
p 
NAME
       scriptreplay - play back typescripts, using timing information

SYNOPSIS
       scriptreplay [options] [-t] timingfile [typescript [divisor]]

```

Or look at the scriptreplay source to see how they handle the timings.

---

### Post by vineshv on 2017-03-23
I had tried this but it is like showing all the content of the file in one shot.
I am expecting something like, first command is 'ls' and second is 'dir'.
And i am waiting for 10 second to execute second 'dir' command.

If i replay the log file then after playing 'ls' command, it should wait for 10 sec to execute 'dir' command.

---

### Post by vineshv on 2017-03-24
please suggest if any solution...

---

### Post by vasa1 on 2017-03-24
> **vineshv said:**
> ...
If i replay the log file then after playing 'ls' command, it should wait for 10 sec to execute 'dir' command.
So you want that the logged commands are actually executed?
```

       The  replay  simply  **displays**  the information again; the programs that
       were run when the typescript was being  recorded  are  **not  run  again**.
       Since  the  same information is simply being displayed, scriptreplay is
       only guaranteed to work properly if run on the same  type  of  terminal
       the  typescript  was  recorded on.  Otherwise, any escape characters in
       the typescript may be interpreted differently by the terminal to  which
       scriptreplay is sending its output.

```from [http://manpages.ubuntu.com/manpages/xenial/en/man1/scriptreplay.1.html](http://manpages.ubuntu.com/manpages/xenial/en/man1/scriptreplay.1.html)

---

