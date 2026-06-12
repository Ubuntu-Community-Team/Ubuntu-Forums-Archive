---
title: "ecryptfs error in syslog"
date: 2016-01-18
forum: General Help
---

### Post by Stormlord on 2016-01-18
Hello all,

Today I noticed these two lines in my system's syslog. I checked all previous log files and I discovered that this error had been logged again twice in the past. On January 16 and on January 11. It appears to be happening approximately 5 minutes after I log in to my user account and it also appears to be happening only this once on every session.

If anyone knows something about this, please share your knowledge ASAP since I'm working heavily on Android development daily and the system has to be 100% reliable. Thanks!

---------------------------------------------------

ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-4]
ecryptfs_write_end: Error encrypting page (upper index [0x00000000000006f3])

---

