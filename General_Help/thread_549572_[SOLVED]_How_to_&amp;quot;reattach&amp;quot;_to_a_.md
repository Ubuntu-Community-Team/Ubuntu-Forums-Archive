---
title: "[SOLVED] How to &amp;quot;reattach&amp;quot; to a &amp;quot;tty ?&amp;quot; job after bg'ing it?"
date: 2007-09-12
forum: General Help
---

### Post by Phrawm48 on 2007-09-12
For "SHELL=/bin/bash", is there a way to bring a background "tty ?" process (nee job) back into the foreground of a _***new***_ terminal window?

[U][B]What I can do:
[/B][/U]If I open a gnome-terminal window and append an ampersand ("&") to a command, the job will run in the background.  If I stay in that terminal window, I can then use the:[LIST]
[*]*jobs* shell(?) command to view that terminal's jobs
[*]*fg* command to bring a numbered job (1, 2, 3,...) back into the foreground
[*]*bg* command to put a numbered job into the background[/LIST][U][B]What I can't do:
[/B][/U]If I close the terminal window and open a new one, the old terminal's background jobs continue running but I can no longer view them with "jobs", let alone use "fg" or "bg" on them.

What I can do at that point is use the new terminal instance to run the process status (*ps*) command, and so list running processes.  However -- the closed terminal's _job_ number no longer exists; instead *ps* provides a process ID ("PID") number.

Moreover -- and more to the point -- the TTY column equals "?".  That is to say, the closed terminal session's TTY information is discarded at the time the session was closed.

[U][B]What I want to do:
[/B][/U]Is it possible to "reattach" a new terminal instance to a "TTY ?" process running in background?   If yes, how?

For example, IF I place a *wget* command in the background, AND close the terminal used to start that job/process, can I open a new terminal window and "reattach" to that running process just as if I'd used the *fg* command to bring it back into the foreground of the original terminal session?

Cheers & thanks,
Ric
SFO

---

### Post by bodhi.zazen on 2007-09-12
You can look at screen

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

		[http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html](http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html)

	[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)


See also dtach :

		[http://ubuntuforums.org/showpost.php?p=3208354&postcount=10](http://ubuntuforums.org/showpost.php?p=3208354&postcount=10)

			dtach -c /tmp/wget wget ....
			dtach -a /tmp/wget

---

### Post by Phrawm48 on 2007-09-12
Wow -- thanks.  This is cool information.  *Screen* offers quite a few possiblities, huh?

The depth and width of the cited material  also makes me feel better about my question.  That is to say, I  evidently wasn't as much of a "silly newbie" as I initially worried I was...

Cheers & thanks 'gain
Ric
SFO

---

