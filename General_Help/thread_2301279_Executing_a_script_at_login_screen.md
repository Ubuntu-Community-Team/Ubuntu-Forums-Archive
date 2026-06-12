---
title: "Executing a script at login screen"
date: 2015-11-01
forum: General Help
---

### Post by Rapacity on 2015-11-01
I'm on 14.04 and I'm trying to execute a script either at the login screen or right after logging in.

Here's the script.

```
#!/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
SHELL=/bin/sh

/sbin/modprobe -r b43 ssb;
/sbin/modprobe ssb;
/sbin/modprobe b43;
/usr/bin/killall wpa_supplicant
/usr/sbin/rfkill unblock all;


```

As of now I've tried two things that haven't worked.

I tried adding the script to rc.local, here's my rc.local

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

(sleep 180 && /bin/wifi_fix) &

exit 0
```

Now when I run sudo /etc/init.d/rc.local start, the script will actually work but when I try to restart the computer it never works.

I've also tried sudo crontab -e, here's the crontab

```
# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
@reboot /bin/wifi_fix >> /home/User003/Documents/wifi_fix_run_test.txt


```

The script doesn't run but it will make that txt file.

Thanks.

---

### Post by Rapacity on 2015-11-01
Update:

so I'm playing around with the crontab again 

I've changed 1 line and added another.

```
* * * * * /bin/wifi_fix >> /home/User003/Desktop/test.txt
@reboot /bin/wifi_fix > /home/User003/Documents/wifi_fix_run_test.txt 2>&1 &
```

so when I try to run the script every minute it works.

and nothing is showing up the txt file so I guess I'm having trouble getting @reboot jobs to run.

---

### Post by Rapacity on 2015-11-01
so it's kind of working now.

I had to chmod 777 the script.

so now I've got this line in my sudo crontab.

```
@reboot (sleep 27 && /bin/wifi_fix > /home/User003/Desktop/wifi_fix_run_test.txt 2>&1) &
```

so it always runs now, it's just the script doesn't always work.

---

### Post by yetimon_64 on 2015-11-01
Personally for simplicity I'd only use the rc.local entry with the commands; ie. NO script or crontab entry.
Using rc.local means the commands will be executed each reboot as root as is required; all those commands require the use of root privileges, so rc.local is fine to use by itself.

Removing the script is only to avoid ownership, permissions & differing shell problems  from the picture. 
Note rc.local is a "sh" script and if used the line "SHELL=" and "PATH=" in the bash script become unnecessary in the rc.local file, the system path for root is already set by the system.

A less complex set up in this case may get things working easier, imo. 

I'd try the rc.local file as below and remove the script and crontab entries altogether. I assume if you manually run all the commands below one at a time in terminal (with sudo for root privileges) as listed below will work ok ... it would pay to check first that they do before relying on the rc.local file. If they do, enter them in rc.local and save and reboot to test this idea.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/sbin/modprobe -r b43 ssb &
/sbin/modprobe ssb &
/sbin/modprobe b43 &
/usr/bin/killall wpa_supplicant &
/usr/sbin/rfkill unblock all &

exit 0


```

Note all processes used are sent to the background with the "&" symbol to prevent a hang up of the boot sequence by rc.local.

Hope this works out for you, good luck. 
Regards, Yeti.

---

### Post by Rapacity on 2015-11-02
Thanks for the reply.

Alright, so I tried your suggestion and removed the crontab entries and everything.

When I just run the commands through rc.local, this will totally disable the wireless.

It's making me think there's a difference between running commands through crontab or rc.local and just typing sudo <command> in the terminal.

I'll keep trying with rc.local, though.

---

### Post by Rapacity on 2015-11-02
Update:

There's nothing actually wrong with using either rc.local or sudo crontab. They both work.

Most of the time when I start up the computer the wireless doesn't work and it gives me these errors in the syslog

```
Nov  2 07:18:06 rapacity-MacBookPro kernel: [   36.472052] b43-phy0 ERROR: DMA RX reset timed out
Nov  2 07:18:07 rapacity-MacBookPro kernel: [   36.656047] b43-phy0 ERROR: DMA TX reset timed out
 
```

but on rare occasions, the computer will start up and the wireless will work and those errors won't be there. This is when either rc.local or crontab entries will work.

I think it's a hardware problem.

Either way, I got my question answered. I know how to execute a script or commands after login or at startup.

Thanks

---

