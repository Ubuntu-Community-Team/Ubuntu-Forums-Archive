---
title: "Zend, Apache2 not working."
date: 2005-10-17
forum: General Help
---

### Post by MindSpore on 2005-10-17
Since I upgraded to Breezy, I cannot get the debugger in Zend Studio to run.  Looks as though it's because Apache won't start.

~$ apache2

(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

How can I fix this?

---

### Post by t2kburl on 2005-10-20
I have the same issue with Apache2


where is there a good howto for using Apache?

---

### Post by MindSpore on 2005-10-20
I just got everything figured out.

Apache2 needs to be executed as root, so do "sudo apache2" to get it to run..

The Zend Debugger needs libtermcap, which had been deprecated, and is not installed in breezy.  So you need to get the termcap-compat with "sudo apt-get install termcap-compat".  

This fixed the debugger, but did not fix my problem.  Finally figured out that Zend Studio Server 10.0.0 was incompatible with php 4.4.x which was had been upgraded with the Breezy upgrade.  So I got Zend Studio Server 10.0.0a, and it fixed the issue.

All working now, hope this helps.

---

