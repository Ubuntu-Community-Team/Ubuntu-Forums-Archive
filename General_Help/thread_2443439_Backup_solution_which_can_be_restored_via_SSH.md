---
title: "Backup solution which can be restored via SSH"
date: 2020-05-15
forum: General Help
---

### Post by tobinhunt on 2020-05-15
How can I setup at cron job backup solution to external storage which I can then restore from via SSH if there's a problem? 

I run a LAMP server remotely, so if I ever need to restore it has to be done remotely too. I see threads saying to boot from a live CD, but how can I do that remotely? Can I partition the internal SSD, install a plain Ubuntu setup there, and if I need to, reboot into that and restore a backup tar.gz from the external drive into the server partition?

---

### Post by TheFu on 2020-05-15
How is the hardware setup initially?  Use the same process to restore.  

Do you have DRAC/RiBLO cards in all the systems - and are those secured beyond the trivial-to-bypass password security? Can someone on-site insert a CD and push the BRS?

Really, backups shouldn't be left connected to the system. They really should be networked, "pulled", and offsite.  Many backup tools support rsync-like network connections and "pulled" backups.

As with all non-trivial answers, there are some choices to be made based on your RTO/RPO requirements.  You can look those terms up on wikipedia.  The goal is to set the appropriate requirements and client expectations.  The more trivial the restore process must be, the more storage and bandwidth has to be wasted.  

Some links
[LIST]
[*]Old Script:  [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) has more discussion.
[*]Restoring backups:  [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[*]aljames2 script w/ LVM snapshots:  [https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233](https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233)
[/LIST]
Local or remote really doesn't matter, once the remote site has a running OS, ssh and whatever backup tool is being used.

Lastly, a tgz file is only appropriate as a backup method for under 500MB of data, not an OS.  it is not useful for versioned backups.

This sounds like a job thing.

---

### Post by HermanAB on 2020-05-15
Maybe see this:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

