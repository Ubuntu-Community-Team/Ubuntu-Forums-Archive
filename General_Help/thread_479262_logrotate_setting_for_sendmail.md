---
title: "logrotate setting for sendmail"
date: 2007-06-20
forum: General Help
---

### Post by tedyeng on 2007-06-20
Hi,

I would like to modify /etc/logrotate.d/sendmail, however the heading of this configuration file says:

# If you're using the stock syslog package, do *NOT* enable anything
# in this file, doing so may result in dual rotations of the logfiles
# and/or loss of logged data.  The syslog package, by default, will
# rotate standard log files based upon various critera !!!

Well, I want to daily rotate sendmail log and reserve 120 rotated log files.

Does anyone know how to do that?

Thank you very much!

---

