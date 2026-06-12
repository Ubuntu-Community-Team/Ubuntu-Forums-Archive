---
title: "Ubuntu hangs on boot"
date: 2008-01-20
forum: General Help
---

### Post by Icemanyurt on 2008-01-20
I am having problems booting into ubuntu.  I can get into safe mode, however I do get this message
> mounting local filesystem
mount: special device dev/disk/by-uuid/c729-cb3b does not exist   [FAIL] 

When I try to start X, I get the error
> run_erl[5117] can't access log directory /usr/lib/erlang/log

When I go into that directory there is no log file, can anyone help?

---

### Post by Icemanyurt on 2008-01-21
bump

---

### Post by mcduck on 2008-01-21
Could you run both 'blkid' and 'cat /etc/fstab' and post the outputs here? Just to check that the UUID is correct..

---

### Post by budhe888 on 2008-01-21
I am having a similar problem.  My system was working fine for a few days after install.  However, after I attempted to hibernate, this problem started occurring.

When trying to bring it out of hibernation, it never came up, so I killed the power and rebooted.  Now, it shows the Ubuntu splash screen, but then right when the gdm login screen normally shows up, I just get the "busy" mouse pointer and a blank screen.  I let that sit for 20 minutes and it does not get any further.

Any ideas?

---

### Post by budhe888 on 2008-01-21
My problem is solved, although it had nothing to do with gdm it seems.  I was in the middle of installing gtk source (for development) and had only installed glib source so far.  Apparently, that was causing it to look for a library that does not exist, making it hang at startup.  Once I uninstalled it, it was fine.

Let's hope that if I install all the part required for gtk (glib, cairo, panko, atk) at once, it then works!

---

