---
title: "Limits.conf"
date: 2005-07-16
forum: General Help
---

### Post by Billybob on 2005-07-16
I need to restrict the number of processes a specific user can have. I went into /etc/security/limits.conf and added this

username hard nproc 400

and I rebooted the machine. However this failed to work. So, uhhh....what do I do?

---

### Post by kvidell on 2005-07-16
From: [http://www.userlocal.com/security/secpam.php](http://www.userlocal.com/security/secpam.php)
----
> #        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
[ ... ]
First we add these lines to restrict user processes to a specified amount given here.

# Limit user processes
*   soft    nproc   100
*   hard    nproc   150My interpretation:
* for any user, kvidell to limit me, or @idiots, to limit a group called "idiots" that you include idiotic users in.

Then you use a "soft" AND a "hard". I'm assuming this is to provide some cushion space for users who honestly aren't being malicious, but are still running a lot of processes.

Hope this helps.
- Kev

---

