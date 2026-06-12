---
title: "Execute command only once at certain time"
date: 2018-12-07
forum: General Help
---

### Post by dam034 on 2018-12-07
Dear users,

I have a .sh file containing a list of commands.

I want to execute that list of commands ("source list.sh") only once at a certain time, e.g. next night at 3 o'clock.

How can I do it?

Thanks

---

### Post by slickymaster on 2018-12-07
Check this thread: [https://stackoverflow.com/questions/5473780/how-to-setup-cron-to-run-a-file-just-once-at-a-specific-time-in-future](https://stackoverflow.com/questions/5473780/how-to-setup-cron-to-run-a-file-just-once-at-a-specific-time-in-future)

---

### Post by btindie on 2018-12-07
For a one off, use the *at* command.

See [https://linuxconfig.org/how-to-schedule-tasks-using-at-command-on-linux](https://linuxconfig.org/how-to-schedule-tasks-using-at-command-on-linux) for an example.

---

### Post by dam034 on 2018-12-08
I read your links and I thought to use "at", instead of "cron".

Now can you give me an example to run "source list.sh" next night at 3 o'clock?

Thanks

---

### Post by yancek on 2018-12-08
Some examples and explanation of using at from the link below. 

[https://linuxconfig.org/how-to-schedule-tasks-using-at-command-on-linux](https://linuxconfig.org/how-to-schedule-tasks-using-at-command-on-linux)

---

### Post by dam034 on 2018-12-08
So is it right this command?

```
at tomorrow - 2 hours -f /srv/commands/list1.sh
```

Thanks

---

### Post by spjackson on 2018-12-09
> **dam034 said:**
> So is it right this command?

```
at tomorrow - 2 hours -f /srv/commands/list1.sh
```

Thanks

It could be, if executed precisely at 5am. A more accurate expression of "next night at 3 o'clock" might be
```
at midnight + 3 hours -f /srv/commands/list1.sh
```

One caveat, the file of commands given via -f (or from standard input) are interpreted by /bin/sh. If list1.sh begins with
```

#!/bin/bash

```
it would still be interpreted by /bin/sh. If this is not what you want then perhaps
```
echo /srv/commands/list1.sh | at midnight + 3 hours
```
might be better.

---

### Post by dam034 on 2018-12-10
What is the difference of interpreting a list by /bin/sh or not?

Thanks

---

### Post by btindie on 2018-12-10
The scripting language available. On Ubuntu, /bin/sh is usually a sym-link to /bin/dash which is not the same as /bin/bash, they're different shells.

If you use
```
echo /srv/commands/list1.sh | at midnight + 3 hours
```
Then make sure the eXecutable bit is set on your script
```
chmod +x list.sh
```

---

