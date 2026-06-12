---
title: "Help with error messages"
date: 2017-03-31
forum: General Help
---

### Post by blkmajik on 2017-03-31
I started getting these errors, not sure what I messed up now :(

[[IMG]http://i.imgur.com/az3RRwG.png[/IMG]]("http://imgur.com/az3RRwG")

---

### Post by blkmajik on 2017-03-31
from /var/log/apport.log

```
ERROR: apport (pid 16282) Fri Mar 31 16:51:08 2017: debug: session gdbus call:
ERROR: apport (pid 16282) Fri Mar 31 16:51:08 2017: this executable already crashed 2 times, ignoring
ERROR: apport (pid 16471) Fri Mar 31 16:55:02 2017: called for pid 16337, signal 11, core limit 0
ERROR: apport (pid 16471) Fri Mar 31 16:55:02 2017: executable: /usr/bin/gnome-photos (command line "/usr/bin/gnome-photos --gapplication-service")
ERROR: apport (pid 16471) Fri Mar 31 16:55:02 2017: debug: session gdbus call: (true,)

ERROR: apport (pid 16471) Fri Mar 31 16:55:07 2017: wrote report /var/crash/_usr_bin_gnome-photos.1000.crash
ERROR: apport (pid 17862) Fri Mar 31 17:08:22 2017: called for pid 17825, signal 11, core limit 0
ERROR: apport (pid 17862) Fri Mar 31 17:08:22 2017: executable: /usr/lib/gnome-settings-daemon/gnome-settings-daemon (command line "/usr/lib/gnome-settings-daemon/gnome-settings-daemon")
ERROR: apport (pid 17862) Fri Mar 31 17:08:22 2017: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 17862) Fri Mar 31 17:08:22 2017: debug: session gdbus call:
ERROR: apport (pid 17862) Fri Mar 31 17:08:22 2017: this executable already crashed 2 times, ignoring


```

---

### Post by blkmajik on 2017-04-01
Can I clear the log like on this site: [http://www.binarytides.com/ubuntu-fix-system-program-problem-error/](http://www.binarytides.com/ubuntu-fix-system-program-problem-error/)

---

### Post by oldos2er on 2017-04-01
Are you running some specific program when the error occurs? I can't make out the details in your screenshot.

---

### Post by blkmajik on 2017-04-06
> **oldos2er said:**
> Are you running some specific program when the error occurs? I can't make out the details in your screenshot.


I wasn't running anything specifically. I would just start the computer  and when logging in I would immediately get the errors. Clearing the log  did rid the errors though

---

