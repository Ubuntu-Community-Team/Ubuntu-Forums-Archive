---
title: "issues with my cronjobs"
date: 2017-10-20
forum: General Help
---

### Post by officeteddy2012 on 2017-10-20
I have installed Ubuntu 16.04.2 LTS

I have written a bash script that if I run it works fine however if I run it under a cronjob it runs multiple times. I have setup the cronjob in root. 
The Job has been setup using crontab -e

I want to run it once on a monday at 11am
__________________________________________________________________
SHELL=/bin/sh PATH=/bin:/sbin:/usr/bin:/usr/sbin


# 1. Entry: Minute when the process will be started [0-60]
# 2. Entry: Hour when the process will be started [0-23]
# 3. Entry: Day of the month when the process will be started [1-28/29/30/31]
# 4. Entry: Month of the year when the process will be started [1-12]
# 5. Entry: Weekday when the process will be started [0-6] [0 is Sunday]
#
# all x min = */x


* 11 * * 1 root bash /srv/scripts/nikesftp.sh
_________________________________________________________________

It also seems when it runs it keeps running over and over where as if I run it manually i runs once? can anyone tell me why

Thanks

matt

---

### Post by steeldriver on 2017-10-20
```

* 11

```

means "every minute of the 11th hour" - to run at once at exactly 11am you want
```

00 11

```
 I think

---

### Post by btindie on 2017-10-20
The crontab entry you've defined means it'll run every minute at 11am on Monday and as it's a users crontab and not a system crontab you can't specify the user it runs as.

So as user *root* do crontab -e
```


0 11 * * 1  /srv/scripts/nikesftp.sh


```

Assuming /srv/scripts/nikesftp.sh begins '#!/bin/bash' and has eXecutable permissions set. That's all you'll need.

Plus /bin/sh is the default SHELL so you don't need to specify that. By default PATH is just 'PATH=/usr/bin:/bin' and you don't need to redefine that if you're not using anything in the sbin directories.

---

