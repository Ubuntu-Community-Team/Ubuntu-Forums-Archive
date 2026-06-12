---
title: "Number of instances of a program being run"
date: 2008-06-16
forum: General Help
---

### Post by r.lopez.negrete on 2008-06-16
Hi all,

I've been managing a multiuser system, and some users tend to abuse and execute 15 to 20 instances of a certain program. Is there anyway I can limit their use to only 1 or 2 instances of the program? 

Any ideas will be welcomed! 

Thanks,
 Rod

---

### Post by HalPomeranz on 2008-06-17
You can limit the total number of simultaneous processes allowed for a given user via /etc/security/limits.conf, but I know of no way to limit users to a certain number of instances of specific processes.  It wouldn't work anyway-- I'd just copy the binary to a different name and run any number of instances under the alternate name(s).

To configure limits.conf, just add a line that looks like one of the following:

```

*                  hard      nproc    32
@users             hard      nproc    32
bob,alice,eve      hard      nproc    32

```

The first line would limit all users (including you) to a maximum of 32 simultaneous processes.  The second line limits all users in group "users" to 32 processes.  The last choice would limit just the listed users.  

Which one you use depends on your environment.  If all your normal users are members of a single group, then the second one is easiest.  If you only have a few users you want to limit, then the last choice is reasonably straightforward.

---

### Post by ibuclaw on 2008-06-17
Also, [read here for some more useful information.]("http://www.cyberciti.biz/tips/linux-limiting-user-process.html")

Although the link isn't specific about the question your asking, it gives some useful info into just how much control you can set in the limits.conf file.

ie:
> **nofile** - max number of open files

And the way you'd set it up would be in the same way as HalPomeranz put it above.
```
@users    hard    nofile    12
```
12 is just an example, you may be as strict or coherant as you wish.

Regards
Iain

---

### Post by r.lopez.negrete on 2008-06-17
Many thanks to both of you! I will read the info and implement it ASAP.
Best regards,
 Rodrigo

---

