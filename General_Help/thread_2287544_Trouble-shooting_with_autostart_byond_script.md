---
title: "Trouble-shooting with autostart byond script"
date: 2015-07-20
forum: General Help
---

### Post by rafael32 on 2015-07-20
i need to do a autostart for my gameserver when the vps reboot or lost connection and him autostart after boot, i tryed this script but dont worked.

When the vps reboot him dont autostart.

i only have ssh acess

> cd
mkdir cron
cd cron
vim launch_mygame.sh

#############Script############
#!/bin/bash
for t in {1..12}
do
    if [ -z "$(ps -C DreamDaemon | grep DreamDaemon)" ]
    then
        /usr/local/bin/DreamDaemon /root/Mygame/NR.dmb port -trusted -logself &
    fi
    sleep 5
done
###################end####################

use the root

sudo su
crontab -e

####inside crontab####
* * * * * /bin/bash /cron/launch_mygame.sh > /dev/null 2>&1

---

