---
title: "/usr/bin/find is slowing down my computer."
date: 2014-01-21
forum: General Help
---

### Post by Rui_Madaleno on 2014-01-21
Hi all,

sometimes my computer slows down nearly to death :(  I can see and hear the hard disk spinning and spinning for a couple of minutes,  hard disk indicator flashing, making my system unusable.

I've done some homework and using Top and Iotop , i've found that sometimes (i cannot explain the interval, start hours ... seems to be random :( ) find command is triggered.
When the find command is triggered i seed a huge amount of read/write in iotop. The attachment to this message shows information taken from system monitor regarding the process running the find command.

[ATTACH=CONFIG]249635[/ATTACH]
Can you help me understand why is the find command running in a random fashion ? how can i prevent it from running ?

best regards

Rui Madalneo

---

### Post by Dave_L on 2014-01-21
To see "who" is running it, here are some ways of displaying a process tree:

```
ps -ejH
```

```
ps axjf
```

```
htop
```

htop (interactive processes viewer) is a package that you may need to install.

---

### Post by Rui_Madaleno on 2014-01-26
Good morning all (just jump out of bed  :) :) :) )

i have more info about the sloooowwwwwwlinessss of my computer.

Using htop and iotop i found the process and the process tree that is causing the performance problem. It's process with PID = 2986 (the blue line in the screenshot bellow)

[ATTACH=CONFIG]249752[/ATTACH]

as far as i understand this process is run in a daily basis by a cron tab job, something related with locatedb ?

Can you give me some guidance to understand this locadb/cron tab job mechanism ? is this some sort of daily disk indexing process to keep an index of files in computer, making searches more quick and effective ? can this be tuned ? can it be change to be run on a weekly basis ?

best regards

Rui Madaleno

---

### Post by sudodus on 2014-01-26
It is creating a database, so that you can search quickly in the file system. What you can do is change the time or interval of the cron job, so that it does not disturb you. For example, if you do not turn off the computer at night, you can let it update the database, and maybe also run an incremental backup of all new and changed files since last backup.

---

### Post by Lars Noodén on 2014-01-26
In your output it shows /etc/cron.daily/locate as the script being run.  You could try moving it to the weekly directory, /etc/cron.weekly  In that way it could be run weekly.

Or, if your machine is on more than just when you are using it, you can change the /etc/crontab file's entry to run daily scripts at a time when they won't bother you.

---

### Post by Dave_L on 2014-01-26
I know the "locate" comand uses that database.  Does anything else use it?

I was going to add a suggestion to run the task using "nice" and/or "ionice".

I checked my /etc/cron.daily directory. (I'm using Ubuntu 12.04.4.) There's no "locate", but there's an "mlocate", and it already uses "ionice" to run at the lowest prioriity.

/etc/cron.daily/mlocate
```
#! /bin/bash

set -e

[ -x /usr/bin/updatedb.mlocate ] || exit 0

if which on_ac_power >/dev/null 2>&1; then
    ON_BATTERY=0
    on_ac_power >/dev/null 2>&1 || ON_BATTERY=$?
    if [ "$ON_BATTERY" -eq 1 ]; then
	exit 0
    fi
fi

##

LOCKFILE="/var/lib/mlocate/daily.lock"

trap "rm -f $LOCKFILE" EXIT

if [ -e "$LOCKFILE" ]; then
    echo >&2 "Warning: $LOCKFILE present, not running updatedb."
    exit 1
else
    touch "$LOCKFILE"
fi

##

# See ionice(1)
if [ -x /usr/bin/ionice ] &&
    /usr/bin/ionice -c3 true 2>/dev/null; then
    IONICE="/usr/bin/ionice -c3"
fi

$IONICE /usr/bin/updatedb.mlocate
```

---

### Post by Rui_Madaleno on 2014-01-29
Hi all,

i've done some homework and learning how cron/crontab works.

In my machine (ubuntu 13.10) i have two daily scripts:

/etc/cron/daily/locate   and  /etc/cron/daily/mlocate

Why these two cron scripts ?

Best regards

Rui Madaleno

---

