---
title: "NIS, Shadow, Pam and FreeBSD"
date: 2007-07-31
forum: General Help
---

### Post by sgbotsford on 2007-07-31
I'm testing edubuntu as a computer lab environment.  Currently my other servers run freebsd.
NIS works on them, and I've got Freebsd's YP Makefile hacked so that it will create a shadow.byname NIS map.

From Serf, the edubunto machine, I can run ypcat shadow.byname as root, and see the data.

I've changed NSswitch.conf to read as follows:
```

passwd:     compat
group:      compat
shadow:     compat

passwd_compat: nis
group_compat: nis
shadow_compat: nis
...{munch}

```

and rebooted.

If I try to login as a NIS user, I can't login.  Pam does not seem to have a way to set a debug level so that you can see WHY the login failed.

Initially I suspected an encryption conflict, so I copied a single user's lines as produced by ypmatch {map} {username} into /etc/passwd and /etc/shadow

Still couldn't login.

Took another look at the files.  Freebsd puts a '*' in the password field of the passwd maps, and it's lookup functions automatically check master.passwd (the equivalent of shadow) 
Linux treats '*' as no login possible, and instead indicates shadow checking with an 'x'

So back to the freebsd YP server, and hack the makefile to put in an 'x' instead of a '*'
Logins now work.

(Sure, you can rant all you want about the security hazards of putting shadow passwords in encrypted form on the network where anyone who can code can slurp them into a cracking program, but I'll point out that with the support for an increased password length the search space is much larger.  If anyone has an inexpensive, robust way to have secure passwords on a mixed network (FreeBSD, linux, window, MacIntosh) please let me know how it's done.)

---

