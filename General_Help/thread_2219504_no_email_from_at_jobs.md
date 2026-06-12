---
title: "no email from at jobs"
date: 2014-04-24
forum: General Help
---

### Post by drdlund on 2014-04-24
I am not getting any email from at jobs. I get email from cron jobs, but none from at jobs. I used to get email from both before I upgraded my system to version 13. If I made changes to a cron job, I could test the changes to the script by running it as an at job instead of waiting for the cron job to fire or dorking with my cron schedule. I thought it was a convenient way to test, and it worked great when I used to get email from both cron and at.

Does anyone know why I would get email from cron but not from at?

Thanks

---

### Post by Danger_Monkey on 2014-04-24
That is a good question.  When using "at", I've either specified the mail command on the command line or within the script that is is executing.

from the command line I would use something like:
```

at (specs) > mail me@here.com < some_text_file

```

I'd be interested in the answer too.

---

