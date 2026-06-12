---
title: "Problem with BackinTime"
date: 2014-03-09
forum: General Help
---

### Post by uwe-bungto on 2014-03-09
Lenovo T61, Xubuntu 12.04 lts, backintime 1.0.34

I have been using Backintime on a laptop with out any problem since  july 2012 .
The last day of Feb in stop backups. 
Message
> [E] Error: rsync: failed to set times on "/mnt/Backups/user-name-backups/backintime/Karen-T61/user-name/1/new_snapshot/backup/home/user-name/user-name/Ubuntu One/Shared With Me": Operation not permitted (1)
[E] Failed to take snapshot 14-03-08 21:56:54 !!!

Ubuntu One was not installed until 2014.03.08 after the problem started to see if it made any difference. It has never been actuated for this user, and probably never will. There is no directory called Ubuntu One/Shared With Me on the T-61 

Any suggestions??

Thanks

Paul

---

### Post by rbmorse on 2014-03-09
Very odd. I've found BackinTime to be pretty robust.  Is that particular directory listed in either the include or exclude sections in BackinTime's settings?

---

### Post by uwe-bungto on 2014-03-12
> **rbmorse said:**
> Very odd. I've found BackinTime to be pretty robust.  Is that particular directory listed in either the include or exclude sections in BackinTime's settings?


it sure is. It has been running without any problem since July 2012.
That directory was listed in the exclude section even though we had never installed ununtuone on that machine

I removed the config file and let backintime build a new one added my in & excludes it has been working ever since.
Must have been a ghost in the machine:confused:

---

