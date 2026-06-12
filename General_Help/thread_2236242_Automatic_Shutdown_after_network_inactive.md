---
title: "Automatic Shutdown after network inactive"
date: 2014-07-25
forum: General Help
---

### Post by hviyer on 2014-07-25
Hi There,

i need to shut down my NAS if there is no network activity for 20 mins. I came accross this code from one of the forums but it doesnt seem to work on my computer and I cant figure out what i'm doing wrong. PLEASE HELP!!

I saved the script in /usr/local/sbin/ForceSleep

```
#!/bin/bash
#
# This is scheduled in CRON.  It will run every 20 minutes
# and check for inactivity.  It compares the RX and TX packets
# from 20 minutes ago to detect if they significantly increased.
# If they haven't, it will force the system to sleep.
# log=~/scripts/idle/log
 # Extract the RX/TX
rx=`/sbin/ifconfig eth0 | grep -m 1 RX | cut -d: -f2 | sed 's/ //g' | sed 's/errors//g'`
tx=`/sbin/ifconfig eth0 | grep -m 1 TX | cut -d: -f2 | sed 's/ //g' | sed 's/errors//g'`
 #Write Date to log
date >> $log
echo "Current Values" >> $log
echo "rx: "$rx >> $log
echo "tx: "$tx >> $log
 # Check if RX/TX Files Exist
if [ -f ~/scripts/idle/rx ] || [ -f ~scripts/idle/tx ]; then
        p_rx=`cat ~/scripts/idle/rx`  ## store previous rx value in p_rx
        p_tx=`cat ~/scripts/idle/tx`  ## store previous tx value in p_tx
         echo "Previous Values" >> $log
        echo "p_rx: "$p_rx >> $log
        echo "t_rx: "$p_tx >> $log
         echo $rx > ~/scripts/idle/rx    ## Write packets to RX file
        echo $tx > ~/scripts/idle/tx    ## Write packets to TX file
         # Calculate threshold limit
        t_rx=`expr $p_rx + 1000`
        t_tx=`expr $p_tx + 1000`
         echo "Threshold Values" >> $log
        echo "t_rx: "$t_rx >> $log
        echo "t_tx: "$t_tx >> $log
        echo " " >> $log
         if [ $rx -le $t_rx ] || [ $tx -le $t_tx ]; then  ## If network packets have not changed that much
                echo "Shutting down" >> $log
                echo " " >> $log
                rm ~/scripts/idle/rx
                rm ~/scripts/idle/tx
                sudo poweroff
        fi
#Check if RX/TX Files Doesn't Exist
else
        echo $rx > ~/scripts/idle/rx ## Write packets to file
        echo $tx > ~/scripts/idle/tx
        echo " " >> $log
fi

 
```

Then in the crontab:
```
crontab -e
```

And in the end of that file to run every 20 mins
```
 */20 * * * * sudo /usr/local/sbin/ForceSleep
```

---

### Post by ian-weisser on 2014-07-25
You should not run cron jobs as sudo. Cron does not know your admin password. You should create a root cron job instead.

---

### Post by hviyer on 2014-07-25
Thanks for your reply.. 

I'm a newbie to Ubuntu and not sure how to run a cron job as a root.. Could anyone pls guide?

---

### Post by ian-weisser on 2014-07-25
Well, there are a couple ways.
The easiest way is
```
sudo crontab -e
```
It will not open _your_ crontab, it will one of root's crontabs. Root, uniquely, has several.

An important element of a crontab is documentation (the comments). Six months from now,you may not remember exactly what you did or how you did it. Keep copious step-by-step notes, links to the instructions you followed, and full paths to the files you edit.
 You may reinstall someday, and want to redo the crontab,
Or your script may be superseded by something better, and you may wish to remove that cron job.

[Advanced]Root's other crontabs are at /etc/crontab and /etc/cron.d/
Only use those if you know what you are doing. They lack a safety net.

---

### Post by hviyer on 2014-07-25
Ok have put it in root cron tab but still no luck! :(

The script works and the system shuts down when I run manually but doesn't work automatically.

---

### Post by ian-weisser on 2014-07-26
> **hviyer said:**
> Ok have put it in root cron tab but still no luck! :(  The script works and the system shuts down when I run manually but doesn't work automatically.  Root does not use your home folder. It's looking for  '~/scripts' in the wrong place. Use full path names.

---

### Post by hviyer on 2014-07-26
Perfect! that now works.. will have now fiddle around with the threshold so that I doesn't shut down when i'm using the machine and not streaming..

Thank You!

---

