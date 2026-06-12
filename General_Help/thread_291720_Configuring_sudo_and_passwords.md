---
title: "Configuring sudo and passwords"
date: 2006-11-02
forum: General Help
---

### Post by rabid emu on 2006-11-02
I don't mind the function of sudo in place of the root account.  However, I'd like sudo to ask for a different password than my account password.  This seems more secure to me than one single password accessing everything on my box.

Also, I've noticed that if I go to the System->Administration menu in gnome, some things there don't ask for a password.  Those that do, ask for my user password.  Is it possible to change which of those asks for a password (so all of them do), and make them all ask for a root password rather than my user password?  For example, I can go to 'users and groups' and access everything there without ever inputting a password (user or otherwise).  Meaning, I can change the root password or permissions of the normal user without inputting any passwords at all!  I think this is really insecure and would like to fix it.

---

### Post by GCR on 2006-11-02
well, you could configure root's password by issuing:

```
passwd root
```
and selecting a password for root. 

Then instead of using *sudo*, you could simply *su* to root while doign administrative tasks. Other was would be to create another user with no priviledges towards the sudoers group.

---

### Post by rabid emu on 2006-11-02
Even if I give my normal user no privileges and give root all privileges, some things still don't ask for a password at all.  How do I fix that?  Also, even if I enable the root account, sudo still asks for the user password so that isn't really a solution.

---

### Post by matthewstory on 2006-11-02
the password thing could just be that sudo remembers that you sudoed for a period of time after you initially sudo, this might be the reason you're only getting a password prompt ever so often.  What you could do is set up a different administrative account, this would be my recommendation.

sudo adduser sysadmin
sudo adduser sysadmin admin
sudo deluser <your user> admin

This will add a user called sysadmin, then add him to the admin group (which is the group with sudo priveleges) then remove your user from the admin group.  Then you just log in as sysadmin when you need to do administrative stuff, or open a terminal as your unpriveleged user, su to sysadmin, and then sudo.

hope this helps.

---

### Post by rabid emu on 2006-11-03
Looks like it will work, but is there any better solution?  Or would that involve rewriting the entire sudo program and whatnot?

Also what about graphical programs (such as those found in the 'system -> administration' menu) that simply don't ask for a password?  To test to see if it was caused by the sudo timeout, I changed it to 0 seconds so it would always ask for a password.  And even after that, the "users and groups" option screen never asks for a password.

---

