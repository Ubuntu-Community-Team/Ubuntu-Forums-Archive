---
title: "&quot;sudo gedit&quot; or &quot;gksudo gedit&quot; no longer works!!!"
date: 2005-10-19
forum: General Help
---

### Post by fizgig on 2005-10-19
I get the following error:

[B](gedit:8558): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/B]


I've seen this in one other post but a solution was never offered.  Anyone have any ideas?

---

### Post by Rogmo on 2005-10-19
Have you tried this:


[http://linux.derkeiler.com/Newsgroups/linux.redhat/2003-09/1193.html](http://linux.derkeiler.com/Newsgroups/linux.redhat/2003-09/1193.html)

---

### Post by fizgig on 2005-10-19
Thanks.  I tried that.  I get this:

matt@Sexylaptop:~$ xroot gedit
Password:
su: Authentication failure
Sorry.

---

### Post by fizgig on 2005-10-20
Well, the problem was that I messed with my network bootup script and the "lo" interface wasn't coming up.  That caused the problem.  All fixed now.

---

