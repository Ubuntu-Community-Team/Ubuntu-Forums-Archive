---
title: "Question about cron and HOME and PATH variables in crontab"
date: 2014-08-22
forum: General Help
---

### Post by bulrush2 on 2014-08-22
Ubuntu 14.04

I'm learning about running crontab, and learned that the path is not setup when my script actually runs. Let's say I have a script called "gocron":

```

#!/bin/bash
set logfile=log.txt
echo `date` >> $logfile

```

This runs fine when I run it from the command prompt. But when I run it via cron, the date/time is not put into /home/chuck/scripts/log.txt. Now let's say my crontab looks like this: 

```

# personal crontab
HOME=/home/chuck/scripts
*/10 * * * * * /home/chuck/scripts/gocron

```

Will cron look for "gocron" under the directory called "/home/chuck/scripts"? If HOME is set, can I have a crontab that looks like this and gocron runs properly and log.txt is updated properly with the date? 

```

# personal crontab
# Run gocron every 10 minutes.
HOME=/home/chuck/scripts
*/10 * * * * * gocron

```

Will an entry be made in /home/chuck/scripts/log.txt? 

Thanks for clarifying. The man pages were not real clear.

---

### Post by Lars Noodén on 2014-08-22
You would need to modify PATH instead of HOME to where you want it to look for additional scripts.  However, I would recommend sticking with using the full paths when calling the scripts.  It makes it more clear later on.

---

