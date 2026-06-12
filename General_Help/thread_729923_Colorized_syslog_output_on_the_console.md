---
title: "Colorized syslog output on the console?"
date: 2008-03-20
forum: General Help
---

### Post by x1a4 on 2008-03-20
Hi,

I'm sending user, daemon and kernel logs to VTs 10-12 and would like to have the output colorized.  Vim does a great job of doing this when I use it to open a log, and I was thinking it might be possible to pipe the output through vim (or something else if it can't be done with vim).  If it's possible, how do I do it?  

BTW, I'm sending the logs to the VTs by having added these lines in /etc/syslog.conf
```

user.*         /dev/tty10
daemon.*       /dev/tty11
kern.*         /dev/tty12

```

Perhaps it's possible to add some more code here to colorize the output?

---

### Post by x1a4 on 2008-03-25
bump :(

---

