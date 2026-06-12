---
title: "crontab not executing my scripts"
date: 2008-04-29
forum: General Help
---

### Post by infocom on 2008-04-29
Hi

I have added a crontab command and when the time comes it doesn't execute my script. I have run a simple test to output the crontab results to a file and it creates the file but its empty. So crontab is running, it creates the output file, but its just not executing my script. The script works when run from command line.

Here's the crontab -l
35 20 * * * /home/userdir/Backups/backup.sh >> /home/userdir/Backups/cronlog.txt

Then when 20:35 came the cronlog.txt file was created but was empty, and my backup.sh script did not execute. 

I have tried this crontab as my user and as root cron jobs, both don't work.

Any ideas appreciated. 
Thanks

---

### Post by infocom on 2008-04-29
Sorry please ignore! I got it working now. My cron command log was logging to a file elsewhere and the test script must have been wrong. It was working all the time.

---

