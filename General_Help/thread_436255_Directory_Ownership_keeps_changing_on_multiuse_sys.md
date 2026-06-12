---
title: "Directory Ownership keeps changing on multiuse system"
date: 2007-05-07
forum: General Help
---

### Post by AmericanAqualung on 2007-05-07
Hi,
I'm partially in charge of maintaining a multiuser system running Ubuntu Dapper.  I have users home directories set to be /n/home/<name> where /n/home is a symlink to /home  (the reason for this is to keep homogeneity with machines that are mounting the users home directories as /n/home/<name> for our cluster).
The issue is that when I run 'ls -l' in /n/home, the privaleged user isn't always who the home folder's name is.  Even if I change it back with chown and wait a few days or so, it reshuffles itself.  No one has logged in in the interm based on my checking of lastlog.  An Example output of the 'ls -l' is:

drwxr-xr-x 2 jdougher        root    4096 2007-03-25 23:35 administrator
drwxr-xr-x 3          1002    users  4096 2007-04-03 20:15 aohara
drwxr-xr-x 3 aohara          users  4096 2007-04-02 18:10 clonderg
drwxr-xr-x 3 mschofie       users  4096 2007-04-02 18:09 jdougher
drwxr-xr-x 4 mshresth      users  4096 2007-04-07 14:00 mschofie
drwxr-xr-x 3          1004    users  4096 2007-03-30 21:01 mshresth
drwxr-xr-x 4 administrator users  4096 2007-04-10 17:08 plove
drwxr-xr-x 3 plove             users  4096 2007-04-02 18:11 rmanning


Is there any way I can permanently fix this?  The only thing I can think of isa chrontab that does this, but I feel like this would be too dirty and not solve the real issue at work here (which I don't have a clue as to what it is).

Thanks,
Andy

---

### Post by abc123456 on 2007-05-08
Check the crontabs for daily, weekly.  When cron runs it could change them.  I hope this helps.:)

---

### Post by justin_guerin on 2007-05-08
I'd recommend making sure /etc/passwd contains the same UID for each user on every system that connects to the share, as well as on the server that hosts the share.  For example, it seems like users 1002 and 1004 aren't known on the machine you grabbed the screen shot from.

---

### Post by AmericanAqualung on 2007-05-10
justin-
after fixing this, everything seems to be clicking properly.  thanks a lot.
-andy

---

