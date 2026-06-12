---
title: "remove regular user account from one time upstart job"
date: 2015-08-12
forum: General Help
---

### Post by roland-logikalsolutions on 2015-08-12
Perplexing little problem. A demo application installed under a regular user account with no privs. An executable under that account owned by root with sticky bit set can be run to "reboot and remove" the demo. The remove.conf file is having a bit of difficulty. I cannot get userdel or deluser to run from within the conf file.

Is it possible to delete a user account from within a one-time upstart job? I tried executing /bin/sh deluser and /bin/sh userdel from the command line and in both cases the commands could not be found. I would really hate to /bin/bash inside of a .conf file.

Anybody else done this?

---

