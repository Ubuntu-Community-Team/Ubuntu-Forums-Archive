---
title: "Cannot have 3 users logged in"
date: 2012-12-08
forum: General Help
---

### Post by jacksaff on 2012-12-08
I have many users who use the same machine. 
Often several of us have used the machine and not logged out. 
THis used to be no problem - the screen gets locked and the next person to use the computer either switches to their old session or starts a new one.

Since the move to lightdm however, any third user to log in gets dumped into a blank screen. 
Ctrl-ALt-F7 gets back to a graphical screen, so things aren't crashing.
 
I suspect that lightdm is trying to start a new session on a virtual terminal that is not set up properly, but I have no idea how to troubleshoot this.

The machine runs the catalyst drivers, and has dual monitors, but as all works ok of vt-7 this doesn't seem to be the problem.

Any ideas?

---

### Post by rnerwein on 2012-12-08
> **jacksaff said:**
> I have many users who use the same machine. 
Often several of us have used the machine and not logged out. 
THis used to be no problem - the screen gets locked and the next person to use the computer either switches to their old session or starts a new one.

Since the move to lightdm however, any third user to log in gets dumped into a blank screen. 
Ctrl-ALt-F7 gets back to a graphical screen, so things aren't crashing.
 
I suspect that lightdm is trying to start a new session on a virtual terminal that is not set up properly, but I have no idea how to troubleshoot this.

The machine runs the catalyst drivers, and has dual monitors, but as all works ok of vt-7 this doesn't seem to be the problem.

Any ideas?

hello
what version of ubuntu are you running, how much memory 
my first idea is --> have anybody manupulatetd the /etc/security/limits.conf ? there are
two options:
1. maxsyslogins - max number of logins on the system
2. maxlogins - max number of logins for this user
on 12.04.1 it's not set by default. i search /proc and /sys but can't find a file to retrieve ors set it.
3. try "who" to see how many tty's and pts are in use.
4. have a look at /etc/securetty
5. what's about your memory ( free command )
6. have a look at the lockfiles in /var/log (just do it after a failed login) 
    tail -40 syslog / kern.log and auth.log

at the moment no more ideas
cheers

---

### Post by jacksaff on 2012-12-08
*what version of ubuntu are you running, how much memory* 

12.10 with 6GB. The system has been updated for several versions, so is likely full of some cruft, but I've never mucked about with any tty config before. 

*have anybody manupulatetd the /etc/security/limits.conf ?*

no, it's all commented out.

*3. try "who" to see how many tty's and pts are in use.*

one tty and 2 pts with just me logged in.

[I]4. have a look at /etc/securetty
[/I]
looks normal, I've never edited it and I suspect it is default. Plenty of ttys declared.

*5. what's about your memory ( free command )*

Not an issue. Also, problem is when third user tries to log in, regardless of level of use. Shouldn't be video memory either  as my card has heaps. Is an hd7870 though, so fairly new with a (perhaps) buggy driver...

*6. have a look at the lockfiles in /var/log (just do it after a failed login)* 

Will do when happens next. 
Not much unusual in /var/log/
I have some errors in auth.log.1 but they appear in the successful logins too.


*at the moment no more ideas*
 
Thank you for the effort!

JS

---

