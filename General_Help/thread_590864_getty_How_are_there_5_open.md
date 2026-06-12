---
title: "getty: How are there 5 open?"
date: 2007-10-25
forum: General Help
---

### Post by oldcpu on 2007-10-25
I was just looking at my `top` and noticed there are 5 getty running.  Why does it need 5?

I did not start these getty manually, so there must be a program that relies on it.  But I do not start any program more than once.

I looked that what these getty does, and it seems to be related to login prompt or something.  Beyond that, I do not know any more.

---

### Post by mannih2001 on 2007-10-25
5 is quite a number, but nothing to worry about. If you really, really want to reduce the number of gettys, you can do what /usr/share/doc/upstart-compat-sysv/README.Debian.gz says: 

How do I reduce the number of gettys?
-------------------------------------

Also see "How do I change which runlevels gettys are run in?"

In /etc/event.d there is a file named ttyN for each getty that will be
started, where N is numbered 1 to 6.  Remove any that you do not
want.

This will not take immediate effect, however you can run "stop ttyN"
to stop one that is running.

---

