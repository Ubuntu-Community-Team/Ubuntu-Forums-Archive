---
title: "can't launch software center or software updater anymore"
date: 2015-10-09
forum: General Help
---

### Post by guine on 2015-10-09
For the past couple of days whenever I've tried to load ubuntu software center or whenever the software updater tried to load for an update either one crashed before it finished loading.  I tried to reinstall software center with this in terminal ```
- sudo apt-get --purge --reinstall install software-center
``` and this is the error I got both times I tried to do a reinstall
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.
```
Any ideas what else I can try to fix this?  Thanks

---

### Post by Yellow Pasque on 2015-10-10
[http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err](http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err)

---

### Post by guine on 2015-10-10
Thanks, that seems to have done the trick.

---

