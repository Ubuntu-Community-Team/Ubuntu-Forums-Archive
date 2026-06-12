---
title: "Backup gone Mad"
date: 2008-04-02
forum: General Help
---

### Post by David Vincent-Jones on 2008-04-02
I installed 'sbackup' directing the data to an external usb drive. I then found that whether I wanted it or not it created a backup every single day without errasing previous creations. I was unable to change the schedule or options.
When my usb drive was not connected it simply flooded my hard drive.
I have now totally deleted sbackup from the system and am using quickstart that appears to work just fine

BUT ...something from sbackup is still creating unwanted backups and flooding my system on a daily basis.

Where do I find the culprit?

---

### Post by gaebriel on 2008-04-03
Have you looked in your /etc/cron* directories? I haven't used sbackup, but just about everything that gets scheduled to run happens by having cron execute a script. If it's happening daily, then it's probably in /etc/cron.daily.

---

### Post by David Vincent-Jones on 2008-04-03
gaebriel;

Thanks for the pointer: Looks like there a bunch of files ... not sure if I can just delete the whole lot but I cannot find a more gracefull way to clear the mess.
   /usr/sbin/backup-manager-purge and -upload
  /etc/cron.daily/backup-manager (looks like the main script)
  /etc/backup-manager.conf           (the config file)
Do you supose I can just trash these files ... there should be a better way!!

---

