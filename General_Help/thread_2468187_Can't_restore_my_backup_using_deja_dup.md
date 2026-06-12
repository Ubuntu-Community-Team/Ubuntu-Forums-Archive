---
title: "Can't restore my backup using deja dup"
date: 2021-10-20
forum: General Help
---

### Post by fhesseti on 2021-10-20
It restores some things, but then it says that it cannot restore the following files and asks me to make sure I can write to them How do I do that? This is what it says. All I want to  do is be able to restore my system, In case it isn't obvious, yes I am a mega noob and I do not know my way around the terminal
[https://i.stack.imgur.com/nwcLR.png](https://i.stack.imgur.com/nwcLR.png)

---

### Post by TheFu on 2021-10-20
50% of Unix is about understanding permissions.  Your userid cannot restore files that aren't owned by your userid.  So, you need to use a userid (or elevate privileges) to an account that can do that.  That's where sudo comes in.  You didn't say which release you are using, so I can't say which sudo options to use. Using the correct option is critical to avoid "I can't login" problems after the restore.  The way that sudo works changed sometime in the last 1-2 yrs, so required options changed too.

Is this a test restore or is this important?  It is always best to test your back up system from time to time, to ensure you know how to restore using it.  After all, "backups" aren't really the important part here.  The "restore" is what this is all about.

I don't use Deja Dup, so someone else will probably need to help. Sorry.

---

