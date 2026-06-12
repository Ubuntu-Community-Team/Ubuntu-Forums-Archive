---
title: "ZFS File Integrity Monitoring Auto"
date: 2023-06-19
forum: General Help
---

### Post by qombi on 2023-06-19
ZFS has diff built in that should be great for file integrity monitoring. I searched around on the internet and read the ZFS diff man pages didn't see a way to schedule diff to run against the most recent snapshot. I would love to get an email with file changes on a schedule. Anyone have an idea how one would do this? Let's say the snapshot is in the format of filename_date (ex. dataset1_230619) that's created daily. I assumed you could setup a cronjob with zfs diff command and pipe to sendmail or something? How would you identify the dynamically named new snapshot? Thanks for any help from the Linux wizs out there.

---

### Post by dragonfly41 on 2023-06-20
This is a first time experiment for me .. and illuminating ..

Browse to [https://phind.com](https://phind.com)   (I recently found this)

Type in your core question as below ..

cronjob with zfs diff command and pipe to sendmail

hit the search button.

---

### Post by MAFoElffen on 2023-06-20
I would use that code as a start of a script called by cron.

But also add in some logic to format your date_stamp for the snapshot names and to ID the name of the last snapshot and current snapshot to do the ZFS Diff. Then error control to tell if the snapshot was created successfully, and how much space remains on storage after the snapshot creation.

These were the kinds of things that were important to me on snapshots and backups jobs. I had the report emailed to my admin account. I wanted a heads up if there was a problem, ad a warnig if I needed to add more storage, or make some changes.

---

### Post by qombi on 2023-06-20
Thanks for sharing that will be a great resource and also thank you for the other suggestions on other attributes I may desire, and I do!

---

### Post by MAFoElffen on 2023-06-20
If you installed ZFS-On-Root via the Ubuntu Desktop ISO, then you have 2 cron jobs scheduled for maintenance as a default. If you installed manually, then you should add these to your crontab...

File /etc/crond.d/zfsutils-linux
```

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# TRIM the first Sunday of every month.
24 0 1-7 * * root if [ $(date +\%w) -eq 0 ] && [ -x /usr/lib/zfs-linux/trim ]; then /usr/lib/zfs-linux/trim; fi

# Scrub the second Sunday of every month.
24 0 8-14 * * root if [ $(date +\%w) -eq 0 ] && [ -x /usr/lib/zfs-linux/scrub ]; then /usr/lib/zfs-linux/scrub; fi

```
That implies that your system should be running at those dates and times, so those jobs run... Otherwise you should run them manually.

---

### Post by qombi on 2023-06-20
Thanks!

---

