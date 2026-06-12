---
title: "Backup with Keep blocks Konqueror processes"
date: 2007-10-22
forum: General Help
---

### Post by AchimRS on 2007-10-22
Hi,
I've installed the backup software Keep and configured several daily backups.
After a reboot a process rdiff-backup blocks konqueror to be "stalled".
This happens several times a day, even if my daily scheduled backup already successful finished that day.
The rdiff-backup process is always be startet and runs on my (old and slow) machine for about 30s and than blocks konqueror for the same time.
When I manually start a "backup now" with Keep, also rdiff-backup process runs but do not blocks any konqueror process.
Do Keep/anacron start the rdiff-backup on each reboot/login with special rights? 

Can anybody help me finding the cron/anacron configuration where the Keep jobs are listed?

I've Keep 0.4 installed on KUbuntu Feisty Fawn. My backup jobs are daily, nice-ed to 19 and connected via SSH auto-login to another machine on network. This creates three processes: rdiff-backup, sh, ssh.

Thanks
Achim

---

