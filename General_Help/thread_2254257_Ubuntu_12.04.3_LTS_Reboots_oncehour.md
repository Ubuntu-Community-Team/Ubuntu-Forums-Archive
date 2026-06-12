---
title: "Ubuntu 12.04.3 LTS Reboots once/hour"
date: 2014-11-25
forum: General Help
---

### Post by Magellan on 2014-11-25
I had this problem when I first installed Ubuntu, and adding acpi=off to my boot command line fixed the problem.  No issues for probably a few years now.
We had a recent power failure, and since then the issue is back!  My computer reboots about once per hour whether or not it is use.  The regularity of the reboot makes me think it's not something like overheating (happens when the computer is idle) or memory issues.

Here's a snippet from my syslog:

> Nov 25 03:17:01 family-desktop CRON[2499]: (root) CMD (   cd / && run-parts --report /etc/cron.
hourly)
Nov 25 03:17:09 family-desktop AptDaemon: INFO: Quitting due to inactivity
Nov 25 03:17:09 family-desktop AptDaemon: INFO: Quitting was requested
Nov 25 03:24:08 family-desktop kernel: [  959.466894] audit_printk_skb: 30 callbacks suppressed
Nov 25 03:24:08 family-desktop kernel: [  959.466898] type=1400 audit(1416914648.523:28): appar
mor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=897 comm="cupsd" pid=89
7 comm="cupsd" capability=36  capname="block_suspend"
Nov 25 04:13:51 family-desktop kernel: imklog 5.8.6, log source = /proc/kmsg started.
Nov 25 04:13:51 family-desktop rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="8
23" x-info="http://www.rsyslog.com"] start
Nov 25 04:13:51 family-desktop rsyslogd: rsyslogd's groupid changed to 103
Nov 25 04:13:51 family-desktop rsyslogd: rsyslogd's userid changed to 101
Nov 25 04:13:51 family-desktop rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try h
ttp://www.rsyslog.com/e/2039 ]
Nov 25 04:13:51 family-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 25 04:13:51 family-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 25 04:13:51 family-desktop kernel: [    0.000000] Linux version 3.8.0-30-generic (buildd@al
lspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #44~precise1-Ubuntu SMP Fri Aug 23 18:32:41 UTC 2013 (Ubuntu 3.8.0-30.44~precise1-generic 3.8.13.6)
Nov 25 04:13:51 family-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-30-generic root=UUID=daee0271-bf1a-401b-a981-558f91f0d942 ro acpi=off quiet splash reboot=bios vt.handoff=7


This pattern repeats in the log every 60 minutes +/- a few seconds.

This is driving me and my family nuts.

Any help is appreciated.

---

### Post by Magellan on 2015-02-11
I think I've figured out a bit of a pattern here.  If I can succesfully shutdown my computer, and then remove the power from it for a long time (say twenty minutes), then the problem seems to go away, but it comes back with th enxt power failure.  Something about the abrupt shut down seems to leave the computer in a strange mode.  

It is hard to get it to shutdown clean when in this mode.  The best I can sometimes due is to force a halt and then kill the power after a while.  I can tell when the problem is rectified as it will boot directly to the splash screen.  When it goes to the grub menu, I know it will shutdown in an hour.

The first good boot also takes a long time.  Maybe 3 minutes before I see the spash screen.  With a bad boot, I'll get to the grub menu pretty fast.

Question:  does anyone know how the comuter can determine a bad shutdown?  I'm starting to think I may have a hardware issues (bad capacitor?).  My thinking is that a if the shutdown process drains a capacitor, then maybe an abtubt shutdown leaves it charged.  The long power down may result in it finally draining.  Total conjecture on my part here, but something I thought I'd ask about.

---

