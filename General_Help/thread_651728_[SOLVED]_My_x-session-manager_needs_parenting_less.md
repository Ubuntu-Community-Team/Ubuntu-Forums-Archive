---
title: "[SOLVED] My x-session-manager needs parenting lessons..."
date: 2007-12-27
forum: General Help
---

### Post by Ertai87 on 2007-12-27
OK, so I've been having this problem today, and with some help from a friend of mine, we narrowed it down to an x-session-manager issue.  If anyone knows of a quick fix, please let me know, otherwise this should probably be put into a bug report for the next update (I don't think regular users can do that, so I'm letting someone know).  Here's the problem:

I am using the program SCIM to do Japanese text input.  On startup, SCIM runs, and creates a process called "scim".  I believe this is the parent process of the various SCIM sub-processes (note all the sub-processes seem to work fine) in that it starts up those processes, but those processes have PPID of 1.

When I run System Monitor, I find that this "scim" process is a zombie.  I don't know why, nor do I really care since it appears to be using no memory or CPU, but the bigger problem is that I can't kill it (I'm a bit of a stickler for not having anything running on my comp that doesn't need to be there, especially zombies).  Here are the steps I've tried and the information I've gotten:

1) I tried ending, stopping, and killing the process.  Nothing works.

2) I tried restarting SCIM from terminal.  The startup "ends abnormally" (whatever that means).

3) I tried uninstalling and reinstalling SCIM.  Upon doing the uninstall, the "scim" process disappeared, so I'm reasonably certain it's not malicious.

4) I tried ps -ef | grep scim, and I found that the process's parent is x-session-manager, and that it's called "[scim] <defunct>".  I tried doing kill -9 on it, but that didn't work either.

Now what really spooks me out is that this happened completely randomly.  I didn't change anything in my configuration.  The way I found this out was I brought my laptop up from standby, and my input had all locked up.  I force-rebooted my computer, checked my system monitor, and this is what happened.

I'm looking for an excuse to say this isn't the work of malicious intent (read: hackers, crackers, or other ne'er-do-wells), and since Linux seems to be relatively secure (plus I'm behind a decent router with a decent key on it), I don't think it is, but I'm still a bit scared since I had security issues on Windows which caused me to switch to Linux in the first place.  Plus I found when I installed Firestarter that my firewall had been off for quite a while, and I haven't gotten any repo updates for quite some time (although everyone I ask says it's normal to not get updates for half a week or so at a time).

So, does anyone have any suggestions on how to fix this, or should I leave it as a bug for the higher-ups to look into?

---

### Post by jken146 on 2007-12-27
This is the third thread I have read where you bring up this issue.  Please be patient and stop making the forums messier!  I even think it may be against the rules.

A google search [http://www.google.com/search?ie=UTF-8&oe=UTF-8&q=zombie+process](http://www.google.com/search?ie=UTF-8&oe=UTF-8&q=zombie+process) should answer your question.

---

### Post by Ertai87 on 2007-12-28
Sorry...I made this thread specifically to give details about this one specific problem with details on what I've done to try and fix it.  I think I'll close this thread now.

---

