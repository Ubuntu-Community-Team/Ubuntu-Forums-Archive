---
title: "Upstart script change has caused subsequent regular shutdown freeze for 5 minutes"
date: 2016-02-01
forum: General Help
---

### Post by nmw01223 on 2016-02-01
I am running MythBuntu 14.04 and the system doesn't shutdown properly any longer.

This occurred following editing the script ... end script section in an Upstart conf file  to do a search for a device at start up, delaying loading of the MythTV backend until it is there. Whilst the code does its job, the result causes a 5 minute delay on shutdown - something is getting stuck, but I am not experienced enough in log files to find it.

Can anyone advise me what to might be and where to look, or even what log file to look in to find the shutdown issue?

The code is as follows:
```

    ....
    echo "`date`" " : Search for HDHR" > /var/log/mythtv/mythtv-backend-start
    for i in `seq 1 30` ; do
        if hdhomerun_config discover >> /var/log/mythtv/mythtv-backend-start ; then
            echo "`date`" " : HDHR detected" >> /var/log/mythtv/mythtv-backend-start
            break
        else
            sleep 1
        fi
    done
    ....

```

Ie it sits in a loop trying to find the device 30 times ('homerun_config discover' returns 0 or 1 depending if it found the device), dropping out when it finds it, or at the end of the loop anyway (timeout).

In fact the script addition can be as simple as 
```

sleep 20

```
and the same thing happens.

---

### Post by nmw01223 on 2016-02-21
Solved, see [http://ubuntuforums.org/showthread.php?t=2312665](http://ubuntuforums.org/showthread.php?t=2312665).

---

