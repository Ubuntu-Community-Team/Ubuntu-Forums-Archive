---
title: "Rsync or Raid 1"
date: 2012-12-17
forum: General Help
---

### Post by williammanda on 2012-12-17
I was looking into backing up a media drive. I wanted to mirror the source so that in the event that the source went bad I could just use the backup drive. I saw that both raid 1 and rsync do this but I'm not very educated in either one. I would like to keep things as simple as possible. I see that rsync has grsync...gui for rsync but there isn't any automatic backups unless the cron is used. I don't know how to do that. Going the raid 1 route....I don't see a gui based program and if I were to use this...could I install the raid 1 and not damage the source drive media? Any help appreciated.

---

### Post by SeijiSensei on 2012-12-17
1)  "RAID is not a substitute for backups."

2)  I'm pretty sure reconfiguring your primary drive to be part of a RAID1 array would require backing everything up, building the array, and restoring the original content. It's not something I'd recommend to a new user.

3)  I'd just set up a "[cron]("https://help.ubuntu.com/community/CronHowto")" job to run rsync overnight and back up the directories that matter.  /home is the most important, but /etc, which contains much of the system's configuration, is another good bet.

---

### Post by Grenage on 2012-12-17
As written, there are pros and cons.

Raid 1 should give you a speed boost, and provide redundancy; it doesn't cover you if the PC's PSU explodes and roasts all of your drives, or if the data getting mirrored is corrupted.

If you must backup to a drive permanently in the machine, it's not a bad way to go - but external backups are king.

---

