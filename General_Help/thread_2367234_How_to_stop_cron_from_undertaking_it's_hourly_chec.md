---
title: "How to stop cron from undertaking it's hourly check"
date: 2017-07-27
forum: General Help
---

### Post by hundred1906 on 2017-07-27
To ensure my system drive drops into idle I think I need to stop cron from doing it's hourly check.

/etc/crontab contains an entry that initiates an hourly check of /etc/cron.hourly. The entry is:
```
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
```

my cron.hourly is empty ( I moved its contents to cron.daily). What is the best way to stop the hourly check or do I just delete the entry?

---

### Post by efflandt on 2017-07-28
Not sure what you mean by dropping your drive into idle, it is always "active/idle" unless you put it into "standby" (which wakes up if you access or mount it), "sleep" (which requires a reset to wake up), or its status is unknown.

If you want to deactivate cron.hourly, simply comment out that line (begin with #) so it is ignored:```
#17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
```

I have a cron.hourly script that puts my /dev/sda (mechanical drive with Win7 and older Ubuntu 14.04) into standby if it is not mounted or already in standby because I cannot seem to be able to set anything with newer drives to go into standby automatically. But I am running from SSD (/dev/sdb). It would be foolish to try to put a drive you are running from or otherwise using into standby because various logging would keep waking it up.```
#!/bin/sh
# Spin down drive(s) when idle and not mounted
# Put script in /etc/cron.hourly
drives="/dev/sda" # drive(s) to spin down (space separated)
IFS="$(printf '\n\t')" # remove newline from hdparm output
for hd in $drives
do
  dstate=$(/sbin/hdparm -C $hd | /bin/grep -B 1 standby)
  if [ $? -ne 0 ] # if not in standby
  then # active/idle
    /bin/grep $hd /etc/mtab 2>&1 > /dev/null
    if [ $? -ne 0 ] # do standby if not mounted
    then dstate=$(/sbin/hdparm -y $hd 2>&1)
    fi 
  fi
  if [ "$dstate" != '' ] # log unless mounted (null)
    then echo $dstate | /usr/bin/logger -e
  fi
done
```Result:```
$ sudo hdparm -C /dev/sda

/dev/sda:
 drive state is:  standby

$ sudo hdparm -C /dev/sdb

/dev/sdb:
 drive state is:  active/idle
```

---

