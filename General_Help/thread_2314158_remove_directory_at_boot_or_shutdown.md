---
title: "remove directory at boot or shutdown"
date: 2016-02-18
forum: General Help
---

### Post by cmcanulty on 2016-02-18
I would like to have a script to remove a directory either at every shutdown or every boot. It is ~.cache/mozilla/firefox/*****.Default User/cache2 I have to do this on multiple machines at a library for privacy reasons. I have cache set to 0 but it doesn't work for cache2. Thank you

---

### Post by newbie-user on 2016-02-19
If the users are using the guest account, doesn't this all get written to tmp anyway? So as long as they log out...

Anyway, here's my attempt at a script:
```

#!/bin/sh
#
#This script removes .cache/mozilla/firefox/* from all users
#
USERS=$(ls /home)

for i in $USERS
     do
          echo "Removing cache2 from $i"
          rm -rf /home/$i/.cache/mozilla/firefox/*
     done
exit 0

```

So the script will look in /home for all users, then remove everything inside the .cache/mozilla/firefox folder for each user.

To have it run at boot and shutdown, put the script in /etc/init.d/ and make it executable, then run:
```
update-rc.d [name of script] defaults 99 01
```

---

### Post by cmcanulty on 2016-02-19
thank you very much will try it and post back

---

