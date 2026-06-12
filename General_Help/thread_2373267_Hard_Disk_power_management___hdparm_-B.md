---
title: "Hard Disk power management   hdparm -B  ?"
date: 2017-10-04
forum: General Help
---

### Post by ra7411 on 2017-10-04
Is anybody familiar with hdparm -B?

Once you set it, does it stay at the same value through suspends, reboots, reinstalls?

It can be set through a span of 1 to 254 - does anyone have know what these levels of settings do?

Thanks

---

### Post by efflandt on 2017-10-04
That worked on older drives, but I don't know if newer drives even support that. It would be easy enough to check by setting it (if that succeeds) and seeing if sudo hdparm -B /dev/sdX (where X is specific drive) without any number shows your previous setting. In my case with 1 TB WD drive:```
~$ sudo hdparm -B /dev/sda

/dev/sda:
 APM_level    = not supported
```Note that it would not make any sense to do that for a drive you are running from, because logging will keep waking up the drive. When I am running from SSD I use this script to put my hard drive in standby (logged to syslog) if it is active and not mounted, otherwise it does nothing (give it execute permission):```
~$ ls -l /etc/cron.hourly
total 4
-rwxr-xr-x 1 root root 602 Jan 25  2017 hd-standby

~$ cat /etc/cron.hourly/hd-standby
#!/bin/sh
# Spin down drive(s) when idle and not mounted
# Put script in /etc/cron.hourly/
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
```

---

### Post by ra7411 on 2017-10-04
>[COLOR=#000000]That worked on older drives, but I don't know if newer drives even support that. It would be easy enough to check by setting it (if that succeeds) and seeing if sudo hdparm -B /dev/sdX (where X is specific drive) without any number shows your previous setting. In my case with 1 TB WD drive:<

It works on my 2 Hitachi HDs (that are infrequently used during the day);  -B "n"  does put them in Standby. I hoped it might be re-setting the drives through suspend, reboot, maybe even an o/s re-install - but no luck. hdparm -B, after suspend/wakeup, showed the drives back in active original state.  
Thanks for the code, but I'll probably continue using Disks to Standby and then unmount those drives. If something got tripped up with the code, I'm too unfamiliar to sort it out without a lot of hassle.

[/COLOR]

---

