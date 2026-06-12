---
title: "Need help with Backup script"
date: 2008-05-22
forum: General Help
---

### Post by laskagifts on 2008-05-22
Hello guys,

Could someone help me to write a simple backup script that backs up all /home directories with this conditions?

1. Script has to use **tar command** to backup the data
2. On Fridays backup should perform FULL backup
3. On Monday though Thursday  the script has to perform differential backup (copy only data that have changed
   since last backup)

4. The script has to find out on which day of the week it is called and has to perform corresponding backup from the 
reference file in /var/log/backup/last-full-backup. This file needs to be updated each time after a full backup

5. For simplicity, backups should be created in this format:
	Full backup		 /tmp/backup-full-YYYY-MM-DD.tar
	Differential backup:     /tmp/backup-diff-YYYY-MM-DD.tar

6.  Log the names of all file saved during the bacup to /var/log/backup/backup-YYYY-MM-DD.log

7. If backup didn't work email should be sent to [email]admin@myserver.com[/email] with subject - Backup Failed


Any help appreciated,

Thanks

---

