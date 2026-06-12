---
title: "Skript called in /etc/pm/sleep.d gets aborded"
date: 2015-03-11
forum: General Help
---

### Post by Robin74 on 2015-03-11
Hello,

I need a script which blocks a programm from sending ubuntu into hibernation for a specified amount of time. This is done by placing a file in /tmp, sleeping for some time and than deleting the file. The Script to create, wait and delete the file reads:
```

#!/bin/bash
echo "$(date) Dateianfang"
touch /tmp/stop_hibernate.continued_from_hibernation
echo "$(date) nach touch"
sleep $1
echo "$(date) nach sleep"
rm -f /tmp/stop_hibernate.continued_from_hibernation
echo "$(date) nach rm"
```
and is located in /usr/local/bin/keep_awake_after_resume and works just fine.

The scripts placed in /etc/pm/sleep.d is called 00_hibernate_resume and reads
```

#!/bin/bash
keepawake=/usr/local/bin/keep_awake_after_resume 
log=/scratch/condor_power_info/resume_$HOSTNAME 
case "$1" in
    suspend|hibernate)
        ;;
    resume|thaw)
        ($keepawake 900 &>> $log &)&
        ;;
    *)
    ;;
esac
```

My Problem is that sometimes it works, in particular if pm-suspend or pm-hibernate is called manually. But sometimes the script gets executed, creates the stop file and is then aborded.

Thank you for your help.
Robin

---

