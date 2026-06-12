---
title: "periodically run a command?"
date: 2008-04-03
forum: General Help
---

### Post by johann_p on 2008-04-03
Is there an easy interactive method to run a command every N seconds and log the output to some file?

I am thinking of something similar to watch, but instead of showing the output fullscreen I simply want to write the output to a file using the standard redirection methods.

So something like "every 10s 'ps | grep xx >> log' " or similar.

---

### Post by sekinto on 2008-04-03
[http://unstableme.blogspot.com/2008/03/execute-program-periodically-bash.html](http://unstableme.blogspot.com/2008/03/execute-program-periodically-bash.html)

---

### Post by mixmaster on 2008-04-03
A simple bash-script loop will do that

#!/bin/bash
while [ 1 ]
do
    ps | grep xxx >> log
    sleep 10
done

---

### Post by FrozenFire on 2008-04-03
What about cron(tab)? xD

---

### Post by njparton on 2008-04-03
I use cron to run several bash scripts once an hour to perform backups using rsync.
 
Seach the forum for advice on crontab.

---

### Post by mixmaster on 2008-04-03
He wanted something run every 10 seconds.  I suppose you could use cron but it seems a bit like overkill

---

