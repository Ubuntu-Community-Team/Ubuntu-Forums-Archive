---
title: "finger reports logged out sessions as idle"
date: 2008-02-01
forum: General Help
---

### Post by PgR on 2008-02-01
When I run finger I'm getting some odd results.

If the user "dave" logs in to tty1, say, then "finger dave" gives ```
Login: dave                             Name: Dave
Directory: /home/dave                   Shell: /bin/bash
On since Fri Feb  1 19:48 (GMT) on tty1   46 seconds idle
     (messages off)
No mail.
No Plan.
```

Reasonable enough. Now if dave logs out, "finger dave" gives ```
Login: dave                             Name: Dave
Directory: /home/dave                   Shell: /bin/bash
On since Fri Feb  1 19:48 (GMT) on tty1   6 minutes 55 seconds idle
     (messages off)
No mail.
No Plan.

```
and finger will show him as being logged in until someone else uses tty1; at which point they adopt this strange ability. Meanwhile tty1 is showing the login prompt.

It does this for all users, and all tty sessions; but not apparently pty. I guess that makes sense.

"who" reports users correctly.

The thing which really bugs me is that gkrellm's "proc" chart seems to use the same source of data as finger. Each time a different tty session is used the number of users shown as active increments, and doesn't decrease when they log out.

Bright ideas?

---

