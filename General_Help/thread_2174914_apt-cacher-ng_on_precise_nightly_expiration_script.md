---
title: "apt-cacher-ng on precise: nightly expiration script throws repeated '502' errors"
date: 2013-09-16
forum: General Help
---

### Post by bikergeek2 on 2013-09-16
I'm running apt-cacher-ng version 0.7.2 on Ubuntu Precise.

Almost every night, I get "502 Resource temporarily unavailable" errors when the nightly expiration script runs.

I don't generally have trouble reaching any Ubuntu repositories when I do upgrades, whether from the command line or using various GUI update tools, so why I'm getting this error is a mystery to me.

Once you get this error, the expiration script will fail forever until you run it manually from the GUI, tag the files that are failing, try the expiration again, lather, rinse, repeat until you succeed.  Often, you have to run it upwards of a dozen times before you finally meet with success.  This is ridiculous.  I wrote the following script as a workaround to loop through and reattempt the expire, and auto-delete the failing files, until the expire script succeeds:

```
#!/bin/bash

cd /var/cache/apt-cacher-ng


/usr/lib/apt-cacher-ng/expire-caller.pl


while [ $? -ne 0 ] ; do
        grep -a1 502 `ls -tr /var/log/apt-cacher-ng/maint_*.log | tail -1` | grep value= | sed -e 's/.*value="\(.*\)">.*/\1/' | xargs rm -v
        echo -n "Waiting 60 seconds to try again..."
        sleep 60
        echo done
        /usr/lib/apt-cacher-ng/expire-caller.pl
done



```

but there has to be a better answer to this.

I'm wondering if what I'm seeing is a variant on this bug, which was fixed in 0.7.4?
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=672801](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=672801)

---

### Post by Eitan_Burcat on 2013-09-17
Same issue here, started in the last couple of days

---

