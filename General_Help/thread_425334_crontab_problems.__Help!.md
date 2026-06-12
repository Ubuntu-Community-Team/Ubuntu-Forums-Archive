---
title: "crontab problems.  Help!"
date: 2007-04-27
forum: General Help
---

### Post by NaughtyusMaximus on 2007-04-27
I'm having horrible problems with vmware and the system clock being off.  My workaround to this is to have the client machine run ntp against the host machine once a minute.

my crontab file looks like this:

0,1,2,3,4,5,6,7,8,9,10, ... 55,56,57,58,59 * * * * /opt/scripts/time

the 'time' script looks like this:

ntpdate vmserver2


If I run the script as root:  sudo /opt/scripts/time , the time is updated correctly.  However, the crontab file doesn't seem to be running often if at all..  I *need* this to work!  Does anyone have any ideas?

---

