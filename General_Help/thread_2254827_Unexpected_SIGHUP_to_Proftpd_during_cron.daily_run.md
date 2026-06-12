---
title: "Unexpected SIGHUP to Proftpd during cron.daily run"
date: 2014-11-30
forum: General Help
---

### Post by JKyleOKC on 2014-11-30
Here's a real puzzler; posting in General Help because it doesn't seem to be appropriate anywhere else.

For two days now, my private FTP server (proftpd) has shut down unexpectedly during or immediately after the morning run of cron.daily -- but there's no task in */etc/cron.daily* that mentions the program.

The last entry in */var/log/ftp.log* is dated November 15; that in itself is strange, because normally the spider robots drop in at least once a week to see if there's anything new.

The logrotate task in cron.daily does rotate logs in */var/log/proftpd*, and forces a restart of the server at weekly and monthly intervals, but that still doesn't explain why the server fails to start during the forced restart action. The logs show that a Signal 15 forced the shutdown, but no following startup appears.

Normally, the server runs standalone 24/7; it has almost no traffic other than the spider visits, but when a potential customer for my data recovery service wants to send me a database file for analysis it's there to receive the file. Yesterday, such a customer attempted to send a pair of files, was unable to connect, and that's how I discovered the problem. I associated it with cron.daily by noting the time of the shutdown as logged in */var/log/proftpd/proftpd.log.1* and comparing to the rotated */var/log/syslog*'s first entry.

Upon manually issuing a restart, the server came back up properly. However, this morning I checked it and found that it had stopped again, at the same second that syslog was rotated.

I'm running Xubuntu 14.04.1 and note that it now uses at least parts of **systemd**; could this be some unwanted side effect of such a change? I also notice that the proftpd-basic file in /etc/logrotate.d uses "*invoke-rc.d* proftpd restart 2>/dev/null >/dev/null || true" to force the restart. Could it be that this is no longer totally valid, and should be changed to invoke "*service*" rather than "invoke-rc.d"?

As I said, it's a real puzzler. Meanwhile I'll wait and see if it goes down on tomorrow's run of cron.daily...

---

### Post by JKyleOKC on 2014-12-01
Bump.

Happened again this morning; here's the /etc/logrotate.d entry that appears to cause it, unchanged for almost a year:```
/var/log/proftpd/proftpd.log 
/var/log/proftpd/controls.log 
{
	weekly
	missingok
	rotate 7
	compress
	delaycompress
	notifempty
	create 640 root adm
	sharedscripts
	postrotate
		# reload could be not sufficient for all logs, a restart is safer
		invoke-rc.d proftpd restart 2>/dev/null >/dev/null || true
	endscript
}

/var/log/proftpd/xferlog
/var/log/proftpd/xferreport
{
	monthly
	missingok
	rotate 7
	compress
	delaycompress
	notifempty
	create 640 root adm
	sharedscripts
	prerotate
	endscript
	postrotate
		# reload could be not sufficient for all logs, a restart is safer
		invoke-rc.d proftpd restart 2>/dev/null >/dev/null || true
		# run ftpstats on past transfer log
		ftpstats -a -r -l 2 -d -h -f /var/log/proftpd/xferlog.0 2>/dev/null >/var/log/proftpd/xferreport || true
	endscript
}

```
And here's the /var/log/proftpd/proftpd.log from this morning's event (the STARTUP was my manual action):```
2014-12-01 06:01:53,545 mehitabel proftpd[28828] mehitabel (62-210-132-6.rev.poneytelecom.eu[62.210.132.6]): FTP session closed.
2014-12-01 07:50:05,526 mehitabel proftpd[22719] mehitabel: ProFTPD killed (signal 15)
2014-12-01 07:50:05,536 mehitabel proftpd[22719] mehitabel: ProFTPD 1.3.5rc3 standalone mode SHUTDOWN
2014-12-01 08:20:07,619 mehitabel proftpd[30472] mehitabel: ProFTPD 1.3.5rc3 (devel) (built Fri Dec 20 2013 18:05:41 UTC) standalone mode STARTUP

```
I'm mystified, and about ready to create a cron.hourly task to restart if stopped...

---

### Post by JKyleOKC on 2014-12-02
Nothing happened this morning, but */var/lib/logrotate/status* showed that logrotate did not run on the proftpd logs today. I think this pins it down firmly to logrotate, but still doesn't answer the question of what is going wrong. Perhaps a bug report is in order.

However I've solved the immediate problem by adding this script to */etc/cron.hourly*:```
#! /bin/bash
#  Script to restart FTP server if not running
#  jk - 2 Dec 2014

s=$(service proftpd status)
r=$(echo "$s"|cut -c 50-56)

logger -p syslog.info "Checking FTP server..." 
if [ "$r" == "running" ]
  then logger -p syslog.info "$s"
  else logger -p syslog.info "$(service proftpd start)"
fi

exit 0

```This assures that the server won't be down for more than an hour. Brute force, but it works...

I'm leaving the thread open in hopes of suggestions from other folk, though.
[COLOR="#FF0000"]
EDIT: Posted bug #1398506 in Launchpad...[/COLOR]

---

