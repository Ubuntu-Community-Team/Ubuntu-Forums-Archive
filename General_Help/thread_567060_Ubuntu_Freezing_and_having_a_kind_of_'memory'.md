---
title: "Ubuntu Freezing and having a kind of 'memory'"
date: 2007-10-04
forum: General Help
---

### Post by SuperAndy on 2007-10-04
My computer will randomly freeze, I dont seem to be able to put a point on when this will happen, as you can see from the system logs below. If the computer locks up, i have no choice but to do a hard reboot. When ubuntu boots, it will then hang again within around 15 minutes of being on. The only way to fix this is to reboot into XP. I can then reboot again into ubuntu, and the problem is gone, at least untill it hangs randomly again.

This first one is the last however many lines from when the computer froze just after i had logged in.

```

Oct  2 12:27:18 andy-desktop dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Oct  2 12:27:18 andy-desktop dhclient: DHCPACK from 192.168.1.1
Oct  2 12:27:18 andy-desktop dhclient: bound to 192.168.1.105 -- renewal in 35529 seconds.
Oct  2 12:39:01 andy-desktop /USR/SBIN/CRON[23097]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 12:59:30 andy-desktop -- MARK --
Oct  2 13:09:01 andy-desktop /USR/SBIN/CRON[24538]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 13:17:01 andy-desktop /USR/SBIN/CRON[24901]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  2 13:39:01 andy-desktop /USR/SBIN/CRON[25884]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 13:59:31 andy-desktop -- MARK --
Oct  2 14:09:01 andy-desktop /USR/SBIN/CRON[27330]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 14:17:01 andy-desktop /USR/SBIN/CRON[27715]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  2 14:39:01 andy-desktop /USR/SBIN/CRON[28749]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 14:59:32 andy-desktop -- MARK --
Oct  2 15:09:01 andy-desktop /USR/SBIN/CRON[30118]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 15:17:01 andy-desktop /USR/SBIN/CRON[30494]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  2 15:39:01 andy-desktop /USR/SBIN/CRON[31524]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 15:59:34 andy-desktop -- MARK --
Oct  2 16:09:01 andy-desktop /USR/SBIN/CRON[400]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 16:17:01 andy-desktop /USR/SBIN/CRON[773]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  2 16:39:01 andy-desktop /USR/SBIN/CRON[1758]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 16:59:35 andy-desktop -- MARK --
Oct  2 17:09:01 andy-desktop /USR/SBIN/CRON[3105]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct  2 17:17:01 andy-desktop /USR/SBIN/CRON[3455]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  2 19:10:51 andy-desktop syslogd 1.4.1#20ubuntu4: restart.

```

The final entry is after i pressed restart.

Below is just before (and one entry after) the computer hung expectadly.

```

Oct  2 19:15:06 andy-desktop anacron[6149]: Normal exit (0 jobs run)
Oct  2 19:15:06 andy-desktop /usr/sbin/cron[6180]: (CRON) INFO (pidfile fd = 3)
Oct  2 19:15:06 andy-desktop /usr/sbin/cron[6181]: (CRON) STARTUP (fork ok)
Oct  2 19:15:06 andy-desktop /usr/sbin/cron[6181]: (CRON) INFO (Running @reboot jobs)
Oct  2 19:15:06 andy-desktop /USR/SBIN/CRON[6207]: (root) CMD (/opt/grisoft/avg7/bin/avgupdate -n --no-daemons --priority 2 --online)
Oct  2 19:15:07 andy-desktop /USR/SBIN/CRON[6206]: (root) MAIL (mailed 182 bytes of output but got status 0x0001 )
Oct  2 19:15:11 andy-desktop gdm[5154]: Restarting computer...
Oct  2 19:15:11 andy-desktop kernel: [   64.372038] mtrr: no MTRR for a0000000,8000000 found
Oct  2 19:15:12 andy-desktop init: tty4 main process (4546) killed by TERM signal
Oct  2 19:15:12 andy-desktop init: tty5 main process (4547) killed by TERM signal
Oct  2 19:15:12 andy-desktop init: tty2 main process (4553) killed by TERM signal
Oct  2 19:15:12 andy-desktop init: tty3 main process (4554) killed by TERM signal
Oct  2 19:15:12 andy-desktop init: tty1 main process (4555) killed by TERM signal
Oct  2 19:15:12 andy-desktop init: tty6 main process (4556) killed by TERM signal
Oct  2 19:15:17 andy-desktop nmbd[5892]: [2007/10/02 19:15:17, 0] nmbd/nmbd.c:terminate(58) 
Oct  2 19:15:17 andy-desktop nmbd[5892]:   Got SIGTERM: going down... 
Oct  2 19:15:19 andy-desktop NetworkManager: <debug info>^I[1191348919.768015] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'). 
Oct  2 19:15:19 andy-desktop NetworkManager: <debug info>^I[1191348919.770686] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct  2 19:15:21 andy-desktop rpc.statd[5976]: Caught signal 15, un-registering and exiting.
Oct  2 19:15:21 andy-desktop mountd[5850]: Caught signal 15, un-registering and exiting.
Oct  2 19:15:21 andy-desktop kernel: [   74.004721] nfsd: last server has exited
Oct  2 19:15:21 andy-desktop kernel: [   74.004724] nfsd: unexporting all filesystems
Oct  2 19:15:21 andy-desktop kernel: [   74.005118] RPC: failed to contact portmap (errno -5).
Oct  2 19:15:21 andy-desktop exiting on signal 15
Oct  2 21:00:14 andy-desktop syslogd 1.4.1#20ubuntu4: restart.

```

Seems to be that gnome has decided its going to reboot, and just stopped responding. But it seems to be something more fundamental, as trying to reboot the x server wont work. The reason for the delay into rebooting was because i rebooted into XP.

Any ideas? BIt of a mystery this is.

---

### Post by SuperAndy on 2007-10-16
Problem seems to be fixed by upgrading to Gutsy.

3 days and no freezing. Looks good so far.

---

### Post by anthonyJC on 2007-10-18
I'm  getting freezing in Gutsy. Frequency of freezing is once every two days.  kernel is untainted. I fount out about PrtScn + RSEIUB, and i'll try that if it happens again in hope i'll get some feedback in the syslog file.

---

### Post by anthonyJC on 2007-11-01
It was caused by dormant fglrx kernel module, i was using radeonhd, but even a dormant fglrx module causes problems. fglrx was still in lsmod list even though i was using radeonhd. it had a (p) after it - i presume that means it was dormant? or only being partially used?

---

