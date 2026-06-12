---
title: "Is file synchronization another source of error?"
date: 2020-02-21
forum: General Help
---

### Post by mrdc76 on 2020-02-21
Let's say I wanted to use Syncthing to synchronize my desktop's and laptop's home folders. Is is possible that a failing SSD would corrupt files on the laptop, and then the corruption would spread to my desktop as they are synchronized?

---

### Post by TheFu on 2020-02-21
yes.

Anything that continuously syncs files between systems can be corrupted when a change causing corruption happens on any of the systems. 

The only mitigation for this issue is versioned backups.  But if you have daily, automatic, encrypted, versioned backups already, then go for it! What's the worst that can happen?  You have to restore a backup copy from the last backup last night or last week or last money sometime.  Backups like this mitigate all sorts of computer issues.

---

### Post by mrdc76 on 2020-02-22
But wouldn't the corruption spread unnoticed to my backups as well? After all, I don't access most of my files regularly. Has this actually happened to someone?

---

### Post by TheFu on 2020-02-22
> **mrdc76 said:**
> But wouldn't the corruption spread unnoticed to my backups as well? After all, I don't access most of my files regularly. Has this actually happened to someone?

VERSIONED backups.  

If we only do clone or mirror backups, then we are screwed.  OTOH, if you have 180 days of daily, versioned, backups, then any corruption should show up as differences in each backup set.  It is pretty clear when that happens in my daily backup reports.  Instead of seeing 30MB of changes, it will have 500 MB or more.  Plus, versioned backups are much, much, quicker to create, even faster than rsync because the backups don't need to recalculate checksums on the target disk.  
[https://ubuntuforums.org/showthread.php?t=2436798&p=13932882#post13932882](https://ubuntuforums.org/showthread.php?t=2436798&p=13932882#post13932882) has some example reports/logs for a machine with times, sizes, plenty of versions.

---

### Post by mrdc76 on 2020-02-22
Thanks, this was really helpful.

---

