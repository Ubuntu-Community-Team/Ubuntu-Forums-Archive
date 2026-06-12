---
title: "[SOLVED] /bin/sh: Syntax error: Bad fd number"
date: 2008-03-29
forum: General Help
---

### Post by davidpbrown on 2008-03-29
Why does a script with #!/bin/bash at the top give an error from /bin/sh?
It runs fine from command line but this error came as mail from a cron job.

I've read a solution.. changing the sym link
```
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh
```
but I'm surprised that's needed.

Are all sudo scripts forced to run through sh to dash, for security etc, ignoring the #!/bin/bash for a reason??

Does changing the /bin/sh affect anything else.. should I maybe learn dash instead of bash??

---

### Post by dcstar on 2008-03-29
> **davidpbrown said:**
> Why does a script with #!/bin/bash at the top give an error from /bin/sh?
It runs fine from command line but this error came as mail from a cron job.

I've read a solution.. changing the sym link
```
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh
```
but I'm surprised that's needed.

Are all sudo scripts forced to run through sh to dash, for security etc, ignoring the #!/bin/bash for a reason??

Does changing the /bin/sh affect anything else.. should I maybe learn dash instead of bash??

Cron jobs run in the environment listed in /etc/crontab

Different shells interpret things differently, if you want things to be the same as you user shell, then change that file rather than deleting binaries.

---

