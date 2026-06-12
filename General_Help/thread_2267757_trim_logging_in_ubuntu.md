---
title: "trim logging in ubuntu?"
date: 2015-03-03
forum: General Help
---

### Post by SirWeazel on 2015-03-03
After searching for hours, i'm unable to find any info.  Everything appears to be outdated or conflicting. I understand that ubuntu now implements trim by a weekly cron job and i've enabled the no model check flag. What i can't find are any log files to verify trim is running and is working correctly. I manually ran ```
sudo fstrim -v /home
``` and ```
sudo fstrim -v /
```
This took a while, and i suspect my drives are not being trimmed like they should. My home is on another drive. Does ```
exec fstrim-all --no-model-check
``` trim all drives?

1. Is this logged somewhere? If not, how can i enable logging to see what drives or partitions are trimmed?
2. If weekly cron jobs like this are missed (computer is off) does the job run automatically when it can?

I used to use a cron job with
```
#!/bin/sh
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
fstrim -v /home >> $LOG

```
Should i revert to this for logging? Thanks for any help.

---

### Post by grahammechanical on 2015-03-03
I cannot help you with logs as I do not have an SSD. Have you seen this?

[http://askubuntu.com/questions/18903/how-to-enable-trim](http://askubuntu.com/questions/18903/how-to-enable-trim)

Regards.

---

### Post by oldfred on 2015-03-04
I turned off the weekly version, and copied my script to the new install in daily cron that is the same as yours. So then I have the log files.
I also looked thru scripts and could not find any logs. And links & logic on checking versions were complicated enough, I just wanted the simple version.

---

### Post by raptir on 2015-03-04
If anacron is installed, Ubuntu will use that instead of cron to run daily, weekly and monthly jobs. You can check that anacron is installed on your system by running...

```

apt-cache policy anacron

```

Or check that it is present and executable through

```

test -x /usr/sbin/anacron && echo OK

```

Assuming anacron is there, it will run your daily, weekly and monthly scripts when the system boots and at least (x) days have passed since the last time those jobs were run. You can check when they are run by looking in your syslog.

```

grep anacron /var/log/syslog

```

Now, none of that tells you the details of what partitions are being trimmed by the fstrim script. You can always edit the fstrim script in /etc/cron.weekly/fstrim if you want to specify the partitions manually, or edit the script to echo the output to a logfile.

---

### Post by SirWeazel on 2015-03-04
Thank you for all the replies. So to sum things up, if i understand correctly.
1. By ubuntu default, the trim command does NOT log anything anywhere. No bytes trimmed, no partitions, or if it even ran at all.
2. It also looks like default ubuntu cron jobs use anacron to run various jobs. These jobs will run when missed. So if the computer is off, and it is a weekly job. If it has been 7 days since last run, it will check this on boot and run the jobs accordingly.

My questions about missed jobs is because i want to make sure a laptop that is powered off often will still be trimmed.

If my home is on a separate drive, should i make sure to specify the home directory like i did in my first post and if it is on the same drive then leave out the home specification?

---

### Post by oldfred on 2015-03-04
Is the other drive also an SSD?

And since trim is run, which erases old data, you cannot recover a deleted file. So good backup practice is essential.

---

### Post by raptir on 2015-03-05
> **SirWeazel said:**
> Thank you for all the replies. So to sum things up, if i understand correctly.
1. By ubuntu default, the trim command does NOT log anything anywhere. No bytes trimmed, no partitions, or if it even ran at all.
2. It also looks like default ubuntu cron jobs use anacron to run various jobs. These jobs will run when missed. So if the computer is off, and it is a weekly job. If it has been 7 days since last run, it will check this on boot and run the jobs accordingly.

My questions about missed jobs is because i want to make sure a laptop that is powered off often will still be trimmed.

If my home is on a separate drive, should i make sure to specify the home directory like i did in my first post and if it is on the same drive then leave out the home specification?

Your understanding is correct. Ubuntu does not log anything with its fstrim job and anacron will ensure that it will run regardless of whether the computer was on at the specified time.

fstrim trims by filesystem, not by disk. So if / and /home are on different partitions, you will want to run it on both. By default, ubuntu runs fstrim --all which will trim all filesystems that support it. You can test the operation by opening a terminal and running:

```
fstrim --all -v
```

to confirm that it does indeed work on your devices.

---

### Post by eezacque on 2015-03-05
As an aside, anacron will tell you when it ran dail/week/monthly, in /var/spool/anacron

---

