---
title: "how do i run a script as root at startup?"
date: 2007-11-09
forum: General Help
---

### Post by jamesford on 2007-11-09
prefereably a few seconds after my desktop has loaded, without having to enter a password?

---

### Post by yabbadabbadont on 2007-11-09
Run it from /etc/rc.local.  It will be the last thing run on boot up, but I can't guarantee that your login screen will be visible before it runs.

---

### Post by jamesford on 2007-11-10
thanks
do i just add a link to my script in that file ? for example:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sleep 40s
/path/to/my/executable/script.sh
exit 0
```

---

### Post by syxbit on 2007-11-10
can't you also do this via crontab?
with the '@reboot' command?

---

### Post by jamesford on 2007-11-10
syxbit,how do u mean? what would such a crontab entry look like?
edit:nm i found out :)

---

### Post by syxbit on 2007-11-10
is that better than doing it via rc.local?

---

### Post by jamesford on 2007-11-10
i dont know. so far so good

---

### Post by RainCT on 2007-11-16
[please delete this]

---

