---
title: "Sudo takes long to ask for password"
date: 2008-06-16
forum: General Help
---

### Post by mmand on 2008-06-16
Sudo seems to take quite a long time before asking for password.

Dell Inspiron 6000; Current Stable Hardy Heron. If you need any more info than that, lemme know.

I've been looking for almost four days for a fix for this, with no luck. Anyone have any ideas? It happens whether I use sudo or gksudo. Seems to take almost 30 seconds to ask for password (if it needs it) or start working (if it doesn't need a password).

I'm also having issues with screen sizes. I have my 19" monitor hooked up and use it as a clone. With Gusty I was able to get 1280 x 1024, but now I can't get above 1024 x 768. I've got the generic crappy Intel video card, if that makes any difference.

Is there some place I can go to find out what hardware is supported 100% (or as close to it as possible)?

Preemptive thanks.

Edit: A few months late, but I found out that it was because my hosts file didn't have my computer name in the loopback line. (127.0.0.1 only had localhost, didn't include my computer name. Fixed it, and it worked just fine.)

---

### Post by cmnorton on 2008-06-17
Have a look to see what else is running on this system, using top or ps.

---

### Post by bingoUV on 2008-06-17
1. Are you using default options for Ubuntu install? i.e. no LDAP, NIS etc.?

2. Instead of bare sudo, use this to trace the syscalls made by sudo into the file /tmp/sudo.trace.out. This opens gedit with root privilege. Do this both when it requires a password and when it doesn't require a password.
```

sudo strace -c -o /tmp/sudo.trace.out sudo gedit

```

Post the file /tmp/sudo.trace.out here so that someone can take a look and advice.

---

