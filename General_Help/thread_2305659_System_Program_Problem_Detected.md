---
title: "System Program Problem Detected"
date: 2015-12-08
forum: General Help
---

### Post by Quarkrad on 2015-12-08
Running 14.04 desktop.  I'm suddenly getting three **System Program Problem Detected** windows on my desktop after boot - as per attached. I know I can turn off the reporting service but I'm not sure whether this is wise in this instance.  I cleared my var/log/syslog file last night and attach the log for this morning.  There is an entry **Will run job `cron.daily' in 5 min** which intrigues me as I'm not aware I have set up any cron jobs, perhaps this is a normal system function.  Is there anything I should be worrying about re these Problem Detected windows?

---

### Post by drm200 on 2015-12-08
I'm suddenly getting the same problem on 14.04 on startup  .... never had it before

---

### Post by Quarkrad on 2015-12-08
I seemed to have solved my problem but I will leave this thread open in case it does not solve yours.  I opened a terminal and used the command sudo rm /var/crash/*sudo rm /var/crash/*   This forum often warns of the dangers of the rm command - as it is dangerous, but in this instance we are only deleting the contents of the var/crash folder.   Try this and see if it solves your problem.

---

