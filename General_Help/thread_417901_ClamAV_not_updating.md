---
title: "ClamAV not updating"
date: 2007-04-22
forum: General Help
---

### Post by Chestnux38 on 2007-04-22
For some reason, when I run a "Freshclam" in the terminal it gives me this

```
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
```

I tried and search for answers, but I can't find any explation or fixes to this.

---

### Post by Famicommie on 2007-04-22
freshclam requires root priveledges. If you ran it with "sudo freshclam", you would not get those errors.

However, running the above command will give you lots of other frightening warnings about ClamAV being out of date. Rest assured that most of the warnings don't matter. Check to see that main.cvd and daily.cvd are up to date. Those are the most important files, and so long as they are indicated as being up to date, you have good protection.

---

### Post by aviceda on 2007-09-21
Hi,

I've just downloaded the 'official'(?) Ubuntu Clamav (0.90)  release and am having similar problems when trying to use freshclam but rather than downloading the latest daily CVD upgrades etc, I get this endless loop,

WARNING: Incremental update failed, trying to download daily.cvd
Ignoring mirror 193.1.193.64 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.202.10.60 (too often connections with outdated version)
ERROR: Can't download daily.cvd from database.clamav.net
Trying again in 5 secs...

Any ideas what to do next?

Tom

---

### Post by dcstar on 2007-09-21
> **aviceda said:**
> Hi,

I've just downloaded the 'official'(?) Ubuntu Clamav (0.90)  release and am having similar problems when trying to use freshclam but rather than downloading the latest daily CVD upgrades etc, I get this endless loop,

WARNING: Incremental update failed, trying to download daily.cvd
Ignoring mirror 193.1.193.64 (too often connections with outdated version)
Ignoring mirror 203.16.234.78 (too often connections with outdated version)
Ignoring mirror 203.202.10.60 (too often connections with outdated version)
ERROR: Can't download daily.cvd from database.clamav.net
Trying again in 5 secs...

Any ideas what to do next?

Tom

Just wait until the servers are less busy, you do not need to manually use freshclam, just installing the packages will download all updates (in their own good time).

---

