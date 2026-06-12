---
title: "HELP! crontab not running this script!"
date: 2008-04-10
forum: General Help
---

### Post by protorox on 2008-04-10
This script runs just fine when it runs in a console...  but when I put it in my crontab, it only kills the running process (first line in script) and then NOTHING happens...

```

#!/bin/bash

# First, kill xwinwrap if already running
killall xwinwrap

# Obtain the number of screensavers in list
RANGE=`wc -l /home/protorox/ss.list|cut -d' ' -f1`

# Create a random number within the range
SSnum=$RANDOM
let "SSnum %= $RANGE"

# Choose the random screensaver to run
SS=`head -$SSnum  /home/protorox/ss.list | tail -1`

# Run xwinwrap with this screensaver
xwinwrap -ni -argb -fs -s -st -sp -nf -b -- $SS -window-id WID &


```

Any suggestions?

---

### Post by Oldsoldier2003 on 2008-04-10
try setting your x session. 
```

 DISPLAY=:0 /somecommand
```
[http://ubuntujourney.wordpress.com/2008/03/25/graphic-applications-in-cronjobs/](http://ubuntujourney.wordpress.com/2008/03/25/graphic-applications-in-cronjobs/)

---

### Post by Oldsoldier2003 on 2008-04-16
the above advice is based on the assumption that it is indeed a graphical application...

---

