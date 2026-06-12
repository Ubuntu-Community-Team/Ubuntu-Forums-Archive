---
title: "Ubuntu 7.10 (gutsy) login problem, timed out after 60 seconds"
date: 2008-01-31
forum: General Help
---

### Post by sudoyang on 2008-01-31
I'm running the Ubuntu 7.10 (Gutsy) server edition.  This is all text-based, no GUI.  For some reason, this morning I can't log in via ssh or at the console  (and I don't have automatic update enabled).  When logging in at the console, the system comes back immediately with a message that login timed out after 60 seconds.  The message is reported immediately after entering the username and password (not after 60 seconds).

When using ssh, this message is reported immediately without a username or password prompt: Connection closed

I know the system is still working because I have several Xen DomU's on the server that are still working just fine (still very responsive).  The only problem is that I can't login to the management host this morning.

Any suggestion except a reboot?  I can't login to the server to poke around.

---

### Post by imkebe on 2008-02-09
Hi, 

Last monday i've power lack and my server restarted. After that I've the same issue - login timeout (info appears after 60 s), ssh connection refuse, http connection reset etc.
Before that i was configuring LDAP so i thought that this is the source of my problem. Instead I've run server in recovery mode and it is all working :confused: I can `su` to my account and run `sudo`. I just need to run all daemons manually to work propetly.

However this is not the solution... I wan't to run my computer normally without this issue. Anybody ?

---

### Post by imkebe on 2008-02-09
I've found the solution (at least for me)... If you had a LDAP configuration try changing /etc/ldap.conf `bind_policy` to `soft`.

[http://ubuntuforums.org/showthread.php?p=3598637](http://ubuntuforums.org/showthread.php?p=3598637)

---

