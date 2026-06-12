---
title: "SBackup Restore Overwrite Option?"
date: 2013-03-01
forum: General Help
---

### Post by Mike Green9 on 2013-03-01
Hi.  (Ubuntu 12.10    Simple Backup 0.11.4)

I backup  /home/mg/   &   /etc/apt/  regularly using SBackup. I had to restore the other day, and realized that SBackup Restore renames files that it is restoring, rather than delete them. This does give me the option to 'revert', but I find it a nuisiance to have to clean up the mess. I tried using these: 

sudo find /home -name *.before_restore* -type f -print0 | xargs -0 /bin/rm -f
sudo find /etc -name *.before_restore* -type f -print0 | xargs -0 /bin/rm -f
   
and it did clean up most, but not all. Is there a way to have SBackup Restore **overwrite** files?

Thanks,

M...

---

