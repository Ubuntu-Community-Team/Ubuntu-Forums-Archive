---
title: "asterisk won't start as daemon"
date: 2008-05-09
forum: General Help
---

### Post by crmccreary on 2008-05-09
I upgraded from dapper to hardy. On dapper, I built asterisk and zaptel and asterisk has been working great. I upgraded to hardy and  installed the asterisk and zaptel packages from the repositories. Reconfigured asterisk and zaptel. Asterisk works fine when I launch it with asterisk -c -vvv from a console but does not function at all as a daemon.

Upon boot, ps -e | grep ast returns safe_asterisk as expected, but there is nothing in the log files (/var/log/messages, var/log/asterisk/messages, or /var/log/daemon.log).

Any suggestions on debugging this? I have to leave a console open with asterisk running for my pbx to be functional. Help appreciated!

---

