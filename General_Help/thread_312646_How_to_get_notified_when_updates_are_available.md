---
title: "How to get notified when updates are available?"
date: 2006-12-04
forum: General Help
---

### Post by naxos on 2006-12-04
Hi,

  I am running Ubuntu on several servers.  I would like to get an email whenever there is are updated packages available.

  Is there a standard way do this? 

  Thanks

---

### Post by missmoondog on 2006-12-04
check daily. updated often. it's no harder to check for updates than it is to open an e-mail.

---

### Post by taurus on 2006-12-04
I don't think there is but you can have aptitude/apt-get running each night using crontab!!!

---

### Post by naxos on 2007-02-12
OK, I'm coming back to this a little late, but here is what I ended up doing.

This two line shell script, run nightly as a cron job, will email me if anything
needs to be updated (I prefer not to update automatically).

/usr/bin/apt-get -qq update
/usr/bin/apt-get -sqq upgrade


the -qq will suppress output unless there are updates available.  The
-s will keep it from actually doing the upgrade.

---

