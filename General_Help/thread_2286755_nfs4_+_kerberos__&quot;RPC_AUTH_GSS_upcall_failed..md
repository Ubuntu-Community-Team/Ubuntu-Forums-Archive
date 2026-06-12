---
title: "nfs4 + kerberos : &quot;RPC: AUTH_GSS upcall failed. Please check user daemon is running.&quot;"
date: 2015-07-14
forum: General Help
---

### Post by rknop on 2015-07-14
I'm cross-mounting various disks between my machines using nsf4 and kerberos (with sec=krb5 and sec=krb5p, depending on the machine).  By and large, things are working.  When a disk is first mounted on a machine, it seems to hang for something like 45 seconds; thereafter, if I try to connect to the machine it's fast.

However, I keep getting this error message in my log file:

[INDENT]RPC: AUTH_GSS upcall failed. Please check user daemon is running.
[/INDENT]

Based on the googling I've done, suggestions are that the problem is a missing rpc.gssd.  However, rpc.gssd and rpc.svcgssd are both running on all of my machines; I'm still getting the error messages.

What could be causing this?

---

### Post by rknop on 2015-07-21
Does anybody have any ideas?

Is there a better forum I could have posted this to?

---

