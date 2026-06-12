---
title: "HP Elitebook 2170P random lockup freeze syslog included"
date: 2014-01-12
forum: General Help
---

### Post by snooze101 on 2014-01-12
Hi

I have a HP Elitebok 2170p running ubuntu 12.04.

This system at random times would lockup, that is, when doing a task on the computer 
the screen would freeze at that moment and 
the sound would continue to repeat (approx 0.3 seconds (lol repeater of course)) itself
the mouse and keyboard inputs no longer work on the system.

The only way to get the system responsive is it do a force reset by pressing and holding down the power switch.

I have included the syslog found on the system when restart is required. (gedit /var/log/syslog/).
[ATTACH]249412[/ATTACH]
Should I be checking another system log for clues to what is causing the system lock ups.

I have included an "enter"/"new line", between when the system was working and the new restart bootup.

Regards
Snooze101

```
Jan 12 06:18:36 l05 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1233" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jan 12 06:18:36 l05 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1233" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jan 12 06:18:39 l05 anacron[1421]: Job `cron.daily' terminated
Jan 12 06:18:39 l05 anacron[1421]: Normal exit (1 job run)
Jan 12 06:24:04 l05 kernel: [ 2113.066562] usb 4-1: USB disconnect, device number 2
Jan 12 06:24:05 l05 kernel: [ 2113.306233] usb 4-1: new SuperSpeed USB device number 3 using xhci_hcd
Jan 12 06:24:05 l05 kernel: [ 2113.322763] hub 4-1:1.0: USB hub found
Jan 12 06:24:05 l05 kernel: [ 2113.322782] hub 4-1:1.0: 4 ports detected
Jan 12 06:25:01 l05 CRON[8057]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Jan 12 06:39:45 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 06:39:46 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 06:39:46 l05 dhclient: bound to 192.168.0.4 -- renewal in 1477 seconds.
Jan 12 06:47:01 l05 CRON[8924]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly ))
Jan 12 07:04:23 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 07:04:24 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 07:04:24 l05 dhclient: bound to 192.168.0.4 -- renewal in 1387 seconds.
Jan 12 07:17:01 l05 CRON[9737]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 07:27:31 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 07:27:32 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 07:27:32 l05 dhclient: bound to 192.168.0.4 -- renewal in 1682 seconds.
Jan 12 07:30:01 l05 CRON[9951]: (root) CMD (start -q anacron || :)
Jan 12 07:30:01 l05 anacron[9954]: Anacron 2.3 started on 2014-01-12
Jan 12 07:30:01 l05 anacron[9954]: Normal exit (0 jobs run)
Jan 12 07:55:34 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 07:55:35 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 07:55:35 l05 dhclient: bound to 192.168.0.4 -- renewal in 1556 seconds.
Jan 12 08:17:02 l05 CRON[11210]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 08:21:31 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 08:21:32 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 08:21:32 l05 dhclient: bound to 192.168.0.4 -- renewal in 1614 seconds.
Jan 12 08:48:26 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 08:48:27 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 08:48:27 l05 dhclient: bound to 192.168.0.4 -- renewal in 1479 seconds.
Jan 12 08:50:31 l05 kernel: [10888.314563] usb 4-1: USB disconnect, device number 3
Jan 12 08:50:31 l05 kernel: [10888.554255] usb 4-1: new SuperSpeed USB device number 4 using xhci_hcd
Jan 12 08:50:31 l05 kernel: [10888.570763] hub 4-1:1.0: USB hub found
Jan 12 08:50:31 l05 kernel: [10888.570787] hub 4-1:1.0: 4 ports detected
Jan 12 09:13:06 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 09:13:07 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 09:13:07 l05 dhclient: bound to 192.168.0.4 -- renewal in 1667 seconds.
Jan 12 09:17:01 l05 CRON[12785]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 09:40:54 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 09:40:55 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 09:40:55 l05 dhclient: bound to 192.168.0.4 -- renewal in 1778 seconds.
Jan 12 10:10:08 l05 gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/hsiva is already mounted
Jan 12 10:10:33 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 10:10:34 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 10:10:34 l05 dhclient: bound to 192.168.0.4 -- renewal in 1367 seconds.
Jan 12 10:17:01 l05 CRON[13979]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 10:33:21 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 10:33:22 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 10:33:22 l05 dhclient: bound to 192.168.0.4 -- renewal in 1393 seconds.
Jan 12 10:56:35 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 10:56:36 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 10:56:36 l05 dhclient: bound to 192.168.0.4 -- renewal in 1439 seconds.
Jan 12 11:17:01 l05 CRON[16162]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 11:20:35 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 11:20:36 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 11:20:36 l05 dhclient: bound to 192.168.0.4 -- renewal in 1467 seconds.
Jan 12 11:32:58 l05 kernel: [20622.633505] Valid eCryptfs headers not found in file header region or xattr region, inode 11541276
Jan 12 11:32:58 l05 kernel: [20622.633627] Valid eCryptfs headers not found in file header region or xattr region, inode 11541263
Jan 12 11:32:58 l05 kernel: [20622.633737] Valid eCryptfs headers not found in file header region or xattr region, inode 11543247
Jan 12 11:45:03 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 11:45:04 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 11:45:04 l05 dhclient: bound to 192.168.0.4 -- renewal in 1413 seconds.
Jan 12 11:54:23 l05 kernel: [21905.702796] device eth0 left promiscuous mode
Jan 12 11:54:23 l05 kernel: [21906.016577] vboxnetflt: 0 out of 0 packets were not sent (directed to host)
Jan 12 11:54:23 l05 kernel: [21906.080489] vboxnetflt: 0 out of 1684299 packets were not sent (directed to host)
Jan 12 12:08:37 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 12:08:38 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 12:08:38 l05 dhclient: bound to 192.168.0.4 -- renewal in 1473 seconds.
Jan 12 12:17:01 l05 CRON[18349]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 12:33:11 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 12:33:12 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 12:33:12 l05 dhclient: bound to 192.168.0.4 -- renewal in 1362 seconds.
Jan 12 12:55:54 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 12:55:55 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 12:55:55 l05 dhclient: bound to 192.168.0.4 -- renewal in 1499 seconds.
Jan 12 13:17:01 l05 CRON[19091]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 13:20:54 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 13:20:55 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 13:20:55 l05 dhclient: bound to 192.168.0.4 -- renewal in 1546 seconds.
Jan 12 13:31:32 l05 kernel: [27727.902654] usb 4-1: USB disconnect, device number 4
Jan 12 13:31:33 l05 kernel: [27728.142322] usb 4-1: new SuperSpeed USB device number 5 using xhci_hcd
Jan 12 13:31:33 l05 kernel: [27728.159138] hub 4-1:1.0: USB hub found
Jan 12 13:31:33 l05 kernel: [27728.159182] hub 4-1:1.0: 4 ports detected
Jan 12 13:46:41 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 13:46:42 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 13:46:42 l05 dhclient: bound to 192.168.0.4 -- renewal in 1562 seconds.
Jan 12 13:53:21 l05 gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/hsiva is already mounted
Jan 12 14:12:44 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 14:12:45 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 14:12:45 l05 dhclient: bound to 192.168.0.4 -- renewal in 1496 seconds.
Jan 12 14:17:01 l05 CRON[20161]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 14:37:41 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 14:37:42 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 14:37:42 l05 dhclient: bound to 192.168.0.4 -- renewal in 1616 seconds.
Jan 12 15:04:38 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 15:04:39 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 15:04:39 l05 dhclient: bound to 192.168.0.4 -- renewal in 1631 seconds.
Jan 12 15:17:01 l05 CRON[21121]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 15:24:21 l05 kernel: [34487.769475] device eth0 entered promiscuous mode
Jan 12 15:31:24 l05 kernel: [34910.040646] device eth0 left promiscuous mode
Jan 12 15:31:24 l05 kernel: [34910.050491] device eth0 entered promiscuous mode
Jan 12 15:31:50 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 15:31:51 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 15:31:51 l05 dhclient: bound to 192.168.0.4 -- renewal in 1592 seconds.
Jan 12 15:42:53 l05 kernel: [35598.097804] usb 4-1: USB disconnect, device number 5
Jan 12 15:42:53 l05 kernel: [35598.337511] usb 4-1: new SuperSpeed USB device number 6 using xhci_hcd
Jan 12 15:42:53 l05 kernel: [35598.354377] hub 4-1:1.0: USB hub found
Jan 12 15:42:53 l05 kernel: [35598.354431] hub 4-1:1.0: 4 ports detected
Jan 12 15:58:23 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 15:58:24 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 15:58:24 l05 dhclient: bound to 192.168.0.4 -- renewal in 1591 seconds.
Jan 12 16:17:01 l05 CRON[27483]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 16:24:55 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 16:24:56 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 16:24:56 l05 dhclient: bound to 192.168.0.4 -- renewal in 1564 seconds.
Jan 12 16:51:00 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 16:51:01 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 16:51:01 l05 dhclient: bound to 192.168.0.4 -- renewal in 1602 seconds.
Jan 12 17:17:01 l05 CRON[29183]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 17:17:43 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 17:17:44 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 17:17:44 l05 dhclient: bound to 192.168.0.4 -- renewal in 1399 seconds.
Jan 12 17:20:52 l05 kernel: [41469.180082] usb 4-1: USB disconnect, device number 6
Jan 12 17:20:52 l05 kernel: [41469.419803] usb 4-1: new SuperSpeed USB device number 7 using xhci_hcd
Jan 12 17:20:52 l05 kernel: [41469.436552] hub 4-1:1.0: USB hub found
Jan 12 17:20:52 l05 kernel: [41469.436594] hub 4-1:1.0: 4 ports detected
Jan 12 17:39:06 l05 kernel: [42562.652980] usb 4-1: USB disconnect, device number 7
Jan 12 17:39:07 l05 kernel: [42562.892813] usb 4-1: new SuperSpeed USB device number 8 using xhci_hcd
Jan 12 17:39:07 l05 kernel: [42562.909658] hub 4-1:1.0: USB hub found
Jan 12 17:39:07 l05 kernel: [42562.909706] hub 4-1:1.0: 4 ports detected
Jan 12 17:41:03 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 17:41:04 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 17:41:04 l05 dhclient: bound to 192.168.0.4 -- renewal in 1509 seconds.
Jan 12 18:06:13 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 18:06:14 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 18:06:14 l05 dhclient: bound to 192.168.0.4 -- renewal in 1570 seconds.
Jan 12 18:17:01 l05 CRON[30019]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 18:25:52 l05 kernel: [45364.199524] usb 4-1: USB disconnect, device number 8
Jan 12 18:25:52 l05 kernel: [45364.439269] usb 4-1: new SuperSpeed USB device number 9 using xhci_hcd
Jan 12 18:25:52 l05 kernel: [45364.456042] hub 4-1:1.0: USB hub found
Jan 12 18:25:52 l05 kernel: [45364.456104] hub 4-1:1.0: 4 ports detected
Jan 12 18:32:24 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 18:32:25 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 18:32:25 l05 dhclient: bound to 192.168.0.4 -- renewal in 1458 seconds.
Jan 12 18:34:30 l05 gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/hsiva is already mounted
Jan 12 18:56:43 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 18:56:44 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 18:56:44 l05 dhclient: bound to 192.168.0.4 -- renewal in 1675 seconds.
Jan 12 19:17:01 l05 CRON[1016]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 19:24:39 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 19:24:40 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 19:24:40 l05 dhclient: bound to 192.168.0.4 -- renewal in 1634 seconds.
Jan 12 19:28:47 l05 gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/hsiva is already mounted
Jan 12 19:51:54 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 19:51:55 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 19:51:55 l05 dhclient: bound to 192.168.0.4 -- renewal in 1672 seconds.
Jan 12 20:17:01 l05 CRON[3289]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 20:19:48 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 20:19:49 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 20:19:49 l05 dhclient: bound to 192.168.0.4 -- renewal in 1376 seconds.
Jan 12 20:30:37 l05 kernel: [52840.065054] usb 4-1: USB disconnect, device number 9
Jan 12 20:30:37 l05 kernel: [52840.304782] usb 4-1: new SuperSpeed USB device number 10 using xhci_hcd
Jan 12 20:30:37 l05 kernel: [52840.321423] hub 4-1:1.0: USB hub found
Jan 12 20:30:37 l05 kernel: [52840.321456] hub 4-1:1.0: 4 ports detected
Jan 12 20:42:45 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 20:42:46 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 20:42:46 l05 dhclient: bound to 192.168.0.4 -- renewal in 1766 seconds.
Jan 12 20:59:22 l05 gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/hsiva is already mounted
Jan 12 21:12:12 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 21:12:13 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 21:12:13 l05 dhclient: bound to 192.168.0.4 -- renewal in 1484 seconds.
Jan 12 21:15:34 l05 kernel: [55533.647314] usb 4-1: USB disconnect, device number 10
Jan 12 21:15:34 l05 kernel: [55533.887063] usb 4-1: new SuperSpeed USB device number 11 using xhci_hcd
Jan 12 21:15:34 l05 kernel: [55533.903867] hub 4-1:1.0: USB hub found
Jan 12 21:15:34 l05 kernel: [55533.903913] hub 4-1:1.0: 4 ports detected
Jan 12 21:17:01 l05 CRON[4784]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 21:36:57 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 12 21:36:58 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 12 21:36:58 l05 dhclient: bound to 192.168.0.4 -- renewal in 1696 seconds.

Jan 12 21:52:34 l05 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jan 12 21:52:34 l05 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1206" x-info="http://www.rsyslog.com"] start
Jan 12 21:52:34 l05 rsyslogd: rsyslogd's groupid changed to 103
Jan 12 21:52:34 l05 rsyslogd: rsyslogd's userid changed to 101
Jan 12 21:52:34 l05 rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jan 12 21:52:34 l05 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 12 21:52:34 l05 kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 12 21:52:34 l05 kernel: [    0.000000] Linux version 3.2.0-58-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 (Ubuntu 3.2.0-58.88-generic 3.2.53)
Jan 12 21:52:34 l05 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic root=UUID=2e4355ef-517f-478a-be6b-63ce5ab552ea ro quiet splash vt.handoff=7
Jan 12 21:52:34 l05 kernel: [    0.000000] KERNEL supported cpus:
Jan 12 21:52:34 l05 kernel: [    0.000000]   Intel GenuineIntel
Jan 12 21:52:34 l05 kernel: [    0.000000]   AMD AuthenticAMD
Jan 12 21:52:34 l05 kernel: [    0.000000]   Centaur CentaurHauls
Jan 12 21:52:34 l05 kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040004000 (usable)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 0000000040004000 - 0000000040005000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 0000000040005000 - 00000000b8b9d000 (usable)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000b8b9d000 - 00000000b9d40000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9d40000 - 00000000b9fb3000 (usable)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fb3000 - 00000000b9fc0000 (ACPI NVS)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fc0000 - 00000000b9fff000 (ACPI data)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fff000 - 00000000ba000000 (usable)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000ba000000 - 00000000bf200000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jan 12 21:52:34 l05 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000023ee00000 (usable)
Jan 12 21:52:34 l05 kernel: [    0.000000] NX (Execute Disable) protection: active
Jan 12 21:52:34 l05 kernel: [    0.000000] SMBIOS 2.7 present.
Jan 12 21:52:34 l05 kernel: [    0.000000] DMI: Hewlett-Packard HP EliteBook 2170p/1815, BIOS 68IMT Ver. F.43 10/07/2013
```

```
Jan 11 06:08:43 l05 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jan 11 06:08:43 l05 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1257" x-info="http://www.rsyslog.com"] start
Jan 11 06:08:43 l05 rsyslogd: rsyslogd's groupid changed to 103
Jan 11 06:08:43 l05 rsyslogd: rsyslogd's userid changed to 101
Jan 11 06:08:43 l05 rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jan 11 06:08:43 l05 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 11 06:08:43 l05 kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 11 06:08:43 l05 kernel: [    0.000000] Linux version 3.2.0-58-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 (Ubuntu 3.2.0-58.88-generic 3.2.53)
Jan 11 06:08:43 l05 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic root=UUID=2e4355ef-517f-478a-be6b-63ce5ab552ea ro quiet splash vt.handoff=7
Jan 11 06:08:43 l05 kernel: [    0.000000] KERNEL supported cpus:
Jan 11 06:08:43 l05 kernel: [    0.000000]   Intel GenuineIntel
Jan 11 06:08:43 l05 kernel: [    0.000000]   AMD AuthenticAMD
Jan 11 06:08:43 l05 kernel: [    0.000000]   Centaur CentaurHauls
Jan 11 06:08:43 l05 kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040004000 (usable)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 0000000040004000 - 0000000040005000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 0000000040005000 - 00000000b8b9d000 (usable)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000b8b9d000 - 00000000b9d40000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9d40000 - 00000000b9fb3000 (usable)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fb3000 - 00000000b9fc0000 (ACPI NVS)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fc0000 - 00000000b9fff000 (ACPI data)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fff000 - 00000000ba000000 (usable)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000ba000000 - 00000000bf200000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000023ee00000 (usable)
Jan 11 06:08:43 l05 kernel: [    0.000000] NX (Execute Disable) protection: active
Jan 11 06:08:43 l05 kernel: [    0.000000] SMBIOS 2.7 present.
Jan 11 06:08:43 l05 kernel: [    0.000000] DMI: Hewlett-Packard HP EliteBook 2170p/1815, BIOS 68IMT Ver. F.43 10/07/2013
Jan 11 06:08:43 l05 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jan 11 06:08:43 l05 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Jan 11 06:08:43 l05 kernel: [    0.000000] No AGP bridge found
Jan 11 06:08:43 l05 kernel: [    0.000000] last_pfn = 0x23ee00 max_arch_pfn = 0x400000000
Jan 11 06:08:43 l05 kernel: [    0.000000] MTRR default type: uncachable
Jan 11 06:08:43 l05 kernel: [    0.000000] MTRR fixed ranges enabled:
Jan 11 06:08:43 l05 kernel: [    0.000000]   00000-9FFFF write-back
Jan 11 06:08:43 l05 kernel: [    0.000000]   A0000-BFFFF uncachable
Jan 11 06:08:43 l05 kernel: [    0.000000]   C0000-FFFFF write-protect
Jan 11 06:08:43 l05 kernel: [    0.000000] MTRR variable ranges enabled:
Jan 11 06:08:43 l05 kernel: [    0.000000]   0 base 0FF800000 mask FFF800000 write-protect
Jan 11 06:08:43 l05 kernel: [    0.000000]   1 base 000000000 mask F80000000 write-back
Jan 11 06:08:43 l05 kernel: [    0.000000]   2 base 080000000 mask FC0000000 write-back
Jan 11 06:08:43 l05 kernel: [    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
Jan 11 06:08:43 l05 kernel: [    0.000000]   4 base 0BB000000 mask FFF000000 uncachable
Jan 11 06:08:43 l05 kernel: [    0.000000]   5 base 100000000 mask F00000000 write-back
Jan 11 06:08:43 l05 kernel: [    0.000000]   6 base 200000000 mask FC0000000 write-back
Jan 11 06:08:43 l05 kernel: [    0.000000]   7 base 23F000000 mask FFF000000 uncachable
Jan 11 06:08:43 l05 kernel: [    0.000000]   8 base 23EE00000 mask FFFE00000 uncachable
Jan 11 06:08:43 l05 kernel: [    0.000000]   9 disabled
Jan 11 06:08:43 l05 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jan 11 06:08:43 l05 kernel: [    0.000000] last_pfn = 0xba000 max_arch_pfn = 0x400000000
Jan 11 06:08:43 l05 kernel: [    0.000000] initial memory mapped : 0 - 20000000
Jan 11 06:08:43 l05 kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
Jan 11 06:08:43 l05 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000ba000000
Jan 11 06:08:43 l05 kernel: [    0.000000]  0000000000 - 00ba000000 page 2M
Jan 11 06:08:43 l05 kernel: [    0.000000] kernel direct mapping tables up to ba000000 @ 1fffc000-20000000
Jan 11 06:08:43 l05 kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000023ee00000
Jan 11 06:08:43 l05 kernel: [    0.000000]  0100000000 - 023ee00000 page 2M
Jan 11 06:08:43 l05 kernel: [    0.000000] kernel direct mapping tables up to 23ee00000 @ b9fad000-b9fb3000
Jan 11 06:08:43 l05 kernel: [    0.000000] RAMDISK: 35820000 - 36c08000
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: RSDP 00000000000f2f10 00024 (v02 HPQOEM)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: XSDT 00000000b9ffe120 0008C (v01 HPQOEM SLIC-MPC 0000000F      01000013)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: FACP 00000000b9ffc000 0010C (v05 HPQOEM 1815     0000000F HP   00000001)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI Warning: FADT (revision 5) is longer than ACPI 2.0 version, truncating length 268 to 244 (20110623/tbfadt-288)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: DSDT 00000000b9fd4000 22D8D (v02 HPQOEM 1815     00000001 INTL 20110112)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: FACS 00000000b9cf5000 00040
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: HPET 00000000b9ffb000 00038 (v01 HPQOEM 1815     00000001 HP   00000001)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: APIC 00000000b9ffa000 000BC (v01 HPQOEM 1815     00000001 HP   00000001)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: MCFG 00000000b9ff9000 0003C (v01 HPQOEM 1815     00000001 HP   00000001)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: TCPA 00000000b9ff7000 00032 (v02 HPQOEM 1815     00000000 HP   00000001)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: SSDT 00000000b9fd1000 002CA (v01 HPQOEM SataAhci 00001000 INTL 20110112)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: SSDT 00000000b9fd0000 0048A (v01 HPQOEM PtidDevc 00001000 INTL 20110112)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: SLIC 00000000b9fcf000 00176 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: FPDT 00000000b9fcd000 00044 (v01 HPQOEM 1815     00000001 HP   00000001)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: BGRT 00000000b9fcc000 00038 (v00 HPQOEM 1815     00000001 HP   00000001)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: SSDT 00000000b9fcb000 009B6 (v01  PmRef  Cpu0Ist 00003000 INTL 20110112)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: SSDT 00000000b9fca000 00AAD (v01  PmRef    CpuPm 00003000 INTL 20110112)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: ASF! 00000000b9ff8000 000A5 (v32 HPQOEM 1815     00000001 HP   00000001)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 11 06:08:43 l05 kernel: [    0.000000] No NUMA configuration found
Jan 11 06:08:43 l05 kernel: [    0.000000] Faking a node at 0000000000000000-000000023ee00000
Jan 11 06:08:43 l05 kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000023ee00000
Jan 11 06:08:43 l05 kernel: [    0.000000]   NODE_DATA [000000023edfb000 - 000000023edfffff]
Jan 11 06:08:43 l05 kernel: [    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880236400000-ffff88023e3fffff] on node 0
Jan 11 06:08:43 l05 kernel: [    0.000000] Zone PFN ranges:
Jan 11 06:08:43 l05 kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan 11 06:08:43 l05 kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jan 11 06:08:43 l05 kernel: [    0.000000]   Normal   0x00100000 -> 0x0023ee00
Jan 11 06:08:43 l05 kernel: [    0.000000] Movable zone start PFN for each node
Jan 11 06:08:43 l05 kernel: [    0.000000] early_node_map[7] active PFN ranges
Jan 11 06:08:43 l05 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Jan 11 06:08:43 l05 kernel: [    0.000000]     0: 0x00000100 -> 0x00020000
Jan 11 06:08:43 l05 kernel: [    0.000000]     0: 0x00020200 -> 0x00040004
Jan 11 06:08:43 l05 kernel: [    0.000000]     0: 0x00040005 -> 0x000b8b9d
Jan 11 06:08:43 l05 kernel: [    0.000000]     0: 0x000b9d40 -> 0x000b9fb3
Jan 11 06:08:43 l05 kernel: [    0.000000]     0: 0x000b9fff -> 0x000ba000
Jan 11 06:08:43 l05 kernel: [    0.000000]     0: 0x00100000 -> 0x0023ee00
Jan 11 06:08:43 l05 kernel: [    0.000000] On node 0 totalpages: 2062749
Jan 11 06:08:43 l05 kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jan 11 06:08:43 l05 kernel: [    0.000000]   DMA zone: 5 pages reserved
Jan 11 06:08:43 l05 kernel: [    0.000000]   DMA zone: 3912 pages, LIFO batch:0
Jan 11 06:08:43 l05 kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Jan 11 06:08:43 l05 kernel: [    0.000000]   DMA32 zone: 736336 pages, LIFO batch:31
Jan 11 06:08:43 l05 kernel: [    0.000000]   Normal zone: 20408 pages used for memmap
Jan 11 06:08:43 l05 kernel: [    0.000000]   Normal zone: 1285704 pages, LIFO batch:31
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Jan 11 06:08:43 l05 kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: IRQ0 used by override.
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: IRQ2 used by override.
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: IRQ9 used by override.
Jan 11 06:08:43 l05 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 11 06:08:43 l05 kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan 11 06:08:43 l05 kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Jan 11 06:08:43 l05 kernel: [    0.000000] nr_irqs_gsi: 40
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000b8b9d000 - 00000000b9d40000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000b9fb3000 - 00000000b9fc0000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000b9fc0000 - 00000000b9fff000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000ba000000 - 00000000bf200000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000bf200000 - 00000000e0000000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Jan 11 06:08:43 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Jan 11 06:08:43 l05 kernel: [    0.000000] Allocating PCI resources starting at bf200000 (gap: bf200000:20e00000)
Jan 11 06:08:43 l05 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan 11 06:08:43 l05 kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
Jan 11 06:08:43 l05 kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88023ea00000 s83136 r8192 d23360 u262144
Jan 11 06:08:43 l05 kernel: [    0.000000] pcpu-alloc: s83136 r8192 d23360 u262144 alloc=1*2097152
Jan 11 06:08:43 l05 kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7
Jan 11 06:08:43 l05 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2025952
Jan 11 06:08:43 l05 kernel: [    0.000000] Policy zone: Normal
Jan 11 06:08:43 l05 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic root=UUID=2e4355ef-517f-478a-be6b-63ce5ab552ea ro quiet splash vt.handoff=7
Jan 11 06:08:43 l05 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jan 11 06:08:43 l05 kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Jan 11 06:08:43 l05 kernel: [    0.000000] Checking aperture...
Jan 11 06:08:43 l05 kernel: [    0.000000] No AGP bridge found
Jan 11 06:08:43 l05 kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jan 11 06:08:43 l05 kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jan 11 06:08:43 l05 kernel: [    0.000000] Memory: 8016740k/9418752k available (6588k kernel code, 1167756k absent, 234256k reserved, 6617k data, 924k init)
Jan 11 06:08:43 l05 kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Jan 11 06:08:43 l05 kernel: [    0.000000] Hierarchical RCU implementation.
Jan 11 06:08:43 l05 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jan 11 06:08:43 l05 kernel: [    0.000000] NR_IRQS:16640 nr_irqs:744 16
Jan 11 06:08:43 l05 kernel: [    0.000000] Extended CMOS year: 2000
Jan 11 06:08:43 l05 kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jan 11 06:08:43 l05 kernel: [    0.000000] Console: colour dummy device 80x25
Jan 11 06:08:43 l05 kernel: [    0.000000] console [tty0] enabled
Jan 11 06:08:43 l05 kernel: [    0.000000] allocated 67108864 bytes of page_cgroup
Jan 11 06:08:43 l05 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan 11 06:08:43 l05 kernel: [    0.000000] hpet clockevent registered
Jan 11 06:08:43 l05 kernel: [    0.000000] Fast TSC calibration failed
Jan 11 06:08:43 l05 kernel: [    0.004000] TSC: PIT calibration matches HPET. 1 loops
Jan 11 06:08:43 l05 kernel: [    0.004000] Detected 2494.051 MHz processor.
Jan 11 06:08:43 l05 kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4988.10 BogoMIPS (lpj=9976204)
Jan 11 06:08:43 l05 kernel: [    0.000007] pid_max: default: 32768 minimum: 301
Jan 11 06:08:43 l05 kernel: [    0.000032] Security Framework initialized
Jan 11 06:08:43 l05 kernel: [    0.000046] AppArmor: AppArmor initialized
Jan 11 06:08:43 l05 kernel: [    0.000047] Yama: becoming mindful.
Jan 11 06:08:43 l05 kernel: [    0.000669] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jan 11 06:08:43 l05 kernel: [    0.003229] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jan 11 06:08:43 l05 kernel: [    0.004356] Mount-cache hash table entries: 256
Jan 11 06:08:43 l05 kernel: [    0.004470] Initializing cgroup subsys cpuacct
Jan 11 06:08:43 l05 kernel: [    0.004474] Initializing cgroup subsys memory
Jan 11 06:08:43 l05 kernel: [    0.004482] Initializing cgroup subsys devices
Jan 11 06:08:43 l05 kernel: [    0.004485] Initializing cgroup subsys freezer
Jan 11 06:08:43 l05 kernel: [    0.004487] Initializing cgroup subsys blkio
Jan 11 06:08:43 l05 kernel: [    0.004492] Initializing cgroup subsys perf_event
Jan 11 06:08:43 l05 kernel: [    0.004523] CPU: Physical Processor ID: 0
Jan 11 06:08:43 l05 kernel: [    0.004524] CPU: Processor Core ID: 0
Jan 11 06:08:43 l05 kernel: [    0.004529] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Jan 11 06:08:43 l05 kernel: [    0.004531] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Jan 11 06:08:43 l05 kernel: [    0.004997] mce: CPU supports 7 MCE banks
Jan 11 06:08:43 l05 kernel: [    0.005010] CPU0: Thermal monitoring enabled (TM1)
Jan 11 06:08:43 l05 kernel: [    0.005019] using mwait in idle threads.
Jan 11 06:08:43 l05 kernel: [    0.007950] ACPI: Core revision 20110623
Jan 11 06:08:43 l05 kernel: [    0.071791] ftrace: allocating 26602 entries in 105 pages
Jan 11 06:08:43 l05 kernel: [    0.082516] x2apic not enabled, IRQ remapping init failed
Jan 11 06:08:43 l05 kernel: [    0.082924] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 11 06:08:43 l05 kernel: [    0.122554] CPU0: Intel(R) Core(TM) i7-3667U CPU @ 2.00GHz stepping 09
Jan 11 06:08:43 l05 kernel: [    0.229821] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
Jan 11 06:08:43 l05 kernel: [    0.229828] ... version:                3
Jan 11 06:08:43 l05 kernel: [    0.229829] ... bit width:              48
Jan 11 06:08:43 l05 kernel: [    0.229830] ... generic registers:      4
Jan 11 06:08:43 l05 kernel: [    0.229832] ... value mask:             0000ffffffffffff
Jan 11 06:08:43 l05 kernel: [    0.229833] ... max period:             000000007fffffff
Jan 11 06:08:43 l05 kernel: [    0.229835] ... fixed-purpose events:   3
Jan 11 06:08:43 l05 kernel: [    0.229836] ... event mask:             000000070000000f
Jan 11 06:08:43 l05 kernel: [    0.229991] NMI watchdog enabled, takes one hw-pmu counter.
Jan 11 06:08:43 l05 kernel: [    0.230075] Booting Node   0, Processors  #1
Jan 11 06:08:43 l05 kernel: [    0.230077] smpboot cpu 1: start_ip = 98000
Jan 11 06:08:43 l05 kernel: [    0.338259] NMI watchdog enabled, takes one hw-pmu counter.
Jan 11 06:08:43 l05 kernel: [    0.338352]  #2
Jan 11 06:08:43 l05 kernel: [    0.338353] smpboot cpu 2: start_ip = 98000
Jan 11 06:08:43 l05 kernel: [    0.446123] NMI watchdog enabled, takes one hw-pmu counter.
Jan 11 06:08:43 l05 kernel: [    0.446203]  #3
Jan 11 06:08:43 l05 kernel: [    0.446204] smpboot cpu 3: start_ip = 98000
Jan 11 06:08:43 l05 kernel: [    0.553973] NMI watchdog enabled, takes one hw-pmu counter.
Jan 11 06:08:43 l05 kernel: [    0.554005] Brought up 4 CPUs
Jan 11 06:08:43 l05 kernel: [    0.554007] Total of 4 processors activated (19953.45 BogoMIPS).
Jan 11 06:08:43 l05 kernel: [    0.559071] devtmpfs: initialized
Jan 11 06:08:43 l05 kernel: [    0.560007] EVM: security.selinux
Jan 11 06:08:43 l05 kernel: [    0.560008] EVM: security.SMACK64
Jan 11 06:08:43 l05 kernel: [    0.560010] EVM: security.capability
Jan 11 06:08:43 l05 kernel: [    0.560035] PM: Registering ACPI NVS region at b9fb3000 (53248 bytes)
Jan 11 06:08:43 l05 kernel: [    0.560873] print_constraints: dummy:
Jan 11 06:08:43 l05 kernel: [    0.560904] RTC time: 19:08:32, date: 01/10/14
Jan 11 06:08:43 l05 kernel: [    0.560936] NET: Registered protocol family 16
Jan 11 06:08:43 l05 kernel: [    0.561035] Trying to unpack rootfs image as initramfs...
Jan 11 06:08:43 l05 kernel: [    0.561044] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Jan 11 06:08:43 l05 kernel: [    0.561047] ACPI: bus type pci registered
Jan 11 06:08:43 l05 kernel: [    0.561124] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jan 11 06:08:43 l05 kernel: [    0.561127] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jan 11 06:08:43 l05 kernel: [    0.627360] PCI: Using configuration type 1 for base access
Jan 11 06:08:43 l05 kernel: [    0.628364] bio: create slab <bio-0> at 0
Jan 11 06:08:43 l05 kernel: [    0.628454] ACPI: Added _OSI(Module Device)
Jan 11 06:08:43 l05 kernel: [    0.628456] ACPI: Added _OSI(Processor Device)
Jan 11 06:08:43 l05 kernel: [    0.628458] ACPI: Added _OSI(3.0 _SCP Extensions)
Jan 11 06:08:43 l05 kernel: [    0.628460] ACPI: Added _OSI(Processor Aggregator Device)
Jan 11 06:08:43 l05 kernel: [    0.630610] ACPI: EC: Look up EC in DSDT
Jan 11 06:08:43 l05 kernel: [    0.633141] ACPI: Executed 1 blocks of module-level executable AML code
Jan 11 06:08:43 l05 kernel: [    0.661284] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jan 11 06:08:43 l05 kernel: [    0.810412] ACPI: SSDT 00000000b9cf3018 00861 (v01  PmRef  Cpu0Cst 00003001 INTL 20110112)
Jan 11 06:08:43 l05 kernel: [    0.810965] ACPI: Dynamic OEM Table Load:
Jan 11 06:08:43 l05 kernel: [    0.810968] ACPI: SSDT           (null) 00861 (v01  PmRef  Cpu0Cst 00003001 INTL 20110112)
Jan 11 06:08:43 l05 kernel: [    0.837262] ACPI: SSDT 00000000b9cf4a98 00303 (v01  PmRef    ApIst 00003000 INTL 20110112)
Jan 11 06:08:43 l05 kernel: [    0.837848] ACPI: Dynamic OEM Table Load:
Jan 11 06:08:43 l05 kernel: [    0.837851] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20110112)
Jan 11 06:08:43 l05 kernel: [    0.869073] ACPI: SSDT 00000000b9cf2d98 00119 (v01  PmRef    ApCst 00003000 INTL 20110112)
Jan 11 06:08:43 l05 kernel: [    0.869619] ACPI: Dynamic OEM Table Load:
Jan 11 06:08:43 l05 kernel: [    0.869622] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20110112)
Jan 11 06:08:43 l05 kernel: [    0.964756] Freeing initrd memory: 20384k freed
Jan 11 06:08:43 l05 kernel: [    1.326110] ACPI: Interpreter enabled
Jan 11 06:08:43 l05 kernel: [    1.326115] ACPI: (supports S0 S3 S4 S5)
Jan 11 06:08:43 l05 kernel: [    1.326142] ACPI: Using IOAPIC for interrupt routing
Jan 11 06:08:43 l05 kernel: [    1.327910] ACPI: Power Resource [APPR] (off)
Jan 11 06:08:43 l05 kernel: [    1.341632] ACPI: Power Resource [COMP] (on)
Jan 11 06:08:43 l05 kernel: [    1.341973] ACPI: Power Resource [LPP] (on)
Jan 11 06:08:43 l05 kernel: [    1.344380] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Jan 11 06:08:43 l05 kernel: [    1.344612] ACPI: No dock devices found.
Jan 11 06:08:43 l05 kernel: [    1.344614] HEST: Table not found.
Jan 11 06:08:43 l05 kernel: [    1.344618] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jan 11 06:08:43 l05 kernel: [    1.345352] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Jan 11 06:08:43 l05 kernel: [    1.345946] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Jan 11 06:08:43 l05 kernel: [    1.345949] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Jan 11 06:08:43 l05 kernel: [    1.345952] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Jan 11 06:08:43 l05 kernel: [    1.345956] pci_root PNP0A08:00: host bridge window [mem 0xbf200000-0xdfffffff]
Jan 11 06:08:43 l05 kernel: [    1.345958] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfedfffff]
Jan 11 06:08:43 l05 kernel: [    1.345960] pci_root PNP0A08:00: host bridge window [mem 0xfee01000-0xffffffff]
Jan 11 06:08:43 l05 kernel: [    1.345973] pci 0000:00:00.0: [8086:0154] type 0 class 0x000600
Jan 11 06:08:43 l05 kernel: [    1.346016] pci 0000:00:02.0: [8086:0166] type 0 class 0x000300
Jan 11 06:08:43 l05 kernel: [    1.346030] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd03fffff 64bit]
Jan 11 06:08:43 l05 kernel: [    1.346038] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
Jan 11 06:08:43 l05 kernel: [    1.346044] pci 0000:00:02.0: reg 20: [io  0x2000-0x203f]
Jan 11 06:08:43 l05 kernel: [    1.346104] pci 0000:00:14.0: [8086:1e31] type 0 class 0x000c03
Jan 11 06:08:43 l05 kernel: [    1.346129] pci 0000:00:14.0: reg 10: [mem 0xd0720000-0xd072ffff 64bit]
Jan 11 06:08:43 l05 kernel: [    1.346206] pci 0000:00:14.0: PME# supported from D3hot D3cold
Jan 11 06:08:43 l05 kernel: [    1.346211] pci 0000:00:14.0: PME# disabled
Jan 11 06:08:43 l05 kernel: [    1.346236] pci 0000:00:16.0: [8086:1e3a] type 0 class 0x000780
Jan 11 06:08:43 l05 kernel: [    1.346262] pci 0000:00:16.0: reg 10: [mem 0xd0734000-0xd073400f 64bit]
Jan 11 06:08:43 l05 kernel: [    1.346346] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Jan 11 06:08:43 l05 kernel: [    1.346350] pci 0000:00:16.0: PME# disabled
Jan 11 06:08:43 l05 kernel: [    1.346376] pci 0000:00:16.3: [8086:1e3d] type 0 class 0x000700
Jan 11 06:08:43 l05 kernel: [    1.346397] pci 0000:00:16.3: reg 10: [io  0x2090-0x2097]
Jan 11 06:08:43 l05 kernel: [    1.346408] pci 0000:00:16.3: reg 14: [mem 0xd073b000-0xd073bfff]
Jan 11 06:08:43 l05 kernel: [    1.346514] pci 0000:00:19.0: [8086:1502] type 0 class 0x000200
Jan 11 06:08:43 l05 kernel: [    1.346534] pci 0000:00:19.0: reg 10: [mem 0xd0700000-0xd071ffff]
Jan 11 06:08:43 l05 kernel: [    1.346544] pci 0000:00:19.0: reg 14: [mem 0xd073a000-0xd073afff]
Jan 11 06:08:43 l05 kernel: [    1.346554] pci 0000:00:19.0: reg 18: [io  0x2060-0x207f]
Jan 11 06:08:43 l05 kernel: [    1.346624] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
Jan 11 06:08:43 l05 kernel: [    1.346628] pci 0000:00:19.0: PME# disabled
Jan 11 06:08:43 l05 kernel: [    1.346654] pci 0000:00:1a.0: [8086:1e2d] type 0 class 0x000c03
Jan 11 06:08:43 l05 kernel: [    1.346677] pci 0000:00:1a.0: reg 10: [mem 0xd0739000-0xd07393ff]
Jan 11 06:08:43 l05 kernel: [    1.346775] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Jan 11 06:08:43 l05 kernel: [    1.346780] pci 0000:00:1a.0: PME# disabled
Jan 11 06:08:43 l05 kernel: [    1.346806] pci 0000:00:1b.0: [8086:1e20] type 0 class 0x000403
Jan 11 06:08:43 l05 kernel: [    1.346823] pci 0000:00:1b.0: reg 10: [mem 0xd0730000-0xd0733fff 64bit]
Jan 11 06:08:43 l05 kernel: [    1.346899] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan 11 06:08:43 l05 kernel: [    1.346903] pci 0000:00:1b.0: PME# disabled
Jan 11 06:08:43 l05 kernel: [    1.346929] pci 0000:00:1c.0: [8086:1e10] type 1 class 0x000604
Jan 11 06:08:43 l05 kernel: [    1.347016] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan 11 06:08:43 l05 kernel: [    1.347021] pci 0000:00:1c.0: PME# disabled
Jan 11 06:08:43 l05 kernel: [    1.347049] pci 0000:00:1c.2: [8086:1e14] type 1 class 0x000604
Jan 11 06:08:43 l05 kernel: [    1.347136] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jan 11 06:08:43 l05 kernel: [    1.347140] pci 0000:00:1c.2: PME# disabled
Jan 11 06:08:43 l05 kernel: [    1.347167] pci 0000:00:1c.3: [8086:1e16] type 1 class 0x000604
Jan 11 06:08:43 l05 kernel: [    1.347254] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jan 11 06:08:43 l05 kernel: [    1.347258] pci 0000:00:1c.3: PME# disabled
Jan 11 06:08:43 l05 kernel: [    1.347293] pci 0000:00:1d.0: [8086:1e26] type 0 class 0x000c03
Jan 11 06:08:43 l05 kernel: [    1.347317] pci 0000:00:1d.0: reg 10: [mem 0xd0738000-0xd07383ff]
Jan 11 06:08:43 l05 kernel: [    1.347416] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Jan 11 06:08:43 l05 kernel: [    1.347421] pci 0000:00:1d.0: PME# disabled
Jan 11 06:08:43 l05 kernel: [    1.347448] pci 0000:00:1f.0: [8086:1e55] type 0 class 0x000601
Jan 11 06:08:43 l05 kernel: [    1.347583] pci 0000:00:1f.2: [8086:1e03] type 0 class 0x000106
Jan 11 06:08:43 l05 kernel: [    1.347603] pci 0000:00:1f.2: reg 10: [io  0x2088-0x208f]
Jan 11 06:08:43 l05 kernel: [    1.347613] pci 0000:00:1f.2: reg 14: [io  0x209c-0x209f]
Jan 11 06:08:43 l05 kernel: [    1.347622] pci 0000:00:1f.2: reg 18: [io  0x2080-0x2087]
Jan 11 06:08:43 l05 kernel: [    1.347631] pci 0000:00:1f.2: reg 1c: [io  0x2098-0x209b]
Jan 11 06:08:43 l05 kernel: [    1.347640] pci 0000:00:1f.2: reg 20: [io  0x2040-0x205f]
Jan 11 06:08:43 l05 kernel: [    1.347648] pci 0000:00:1f.2: reg 24: [mem 0xd0737000-0xd07377ff]
Jan 11 06:08:43 l05 kernel: [    1.347699] pci 0000:00:1f.2: PME# supported from D3hot
Jan 11 06:08:43 l05 kernel: [    1.347703] pci 0000:00:1f.2: PME# disabled
Jan 11 06:08:43 l05 kernel: [    1.347772] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
Jan 11 06:08:43 l05 kernel: [    1.347779] pci 0000:00:1c.0:   bridge window [mem 0xd0600000-0xd06fffff]
Jan 11 06:08:43 l05 kernel: [    1.347859] pci 0000:02:00.0: [197b:2392] type 0 class 0x000880
Jan 11 06:08:43 l05 kernel: [    1.347886] pci 0000:02:00.0: reg 10: [mem 0xd0503000-0xd05030ff]
Jan 11 06:08:43 l05 kernel: [    1.348002] pci 0000:02:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
Jan 11 06:08:43 l05 kernel: [    1.348150] pci 0000:02:00.2: [197b:2391] type 0 class 0x000805
Jan 11 06:08:43 l05 kernel: [    1.348178] pci 0000:02:00.2: reg 10: [mem 0xd0502000-0xd05020ff]
Jan 11 06:08:43 l05 kernel: [    1.356940] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
Jan 11 06:08:43 l05 kernel: [    1.356947] pci 0000:00:1c.2:   bridge window [mem 0xd0500000-0xd05fffff]
Jan 11 06:08:43 l05 kernel: [    1.357164] pci 0000:03:00.0: [8086:088e] type 0 class 0x000280
Jan 11 06:08:43 l05 kernel: [    1.357315] pci 0000:03:00.0: reg 10: [mem 0xd0400000-0xd0401fff 64bit]
Jan 11 06:08:43 l05 kernel: [    1.358056] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Jan 11 06:08:43 l05 kernel: [    1.358092] pci 0000:03:00.0: PME# disabled
Jan 11 06:08:43 l05 kernel: [    1.365008] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
Jan 11 06:08:43 l05 kernel: [    1.365016] pci 0000:00:1c.3:   bridge window [mem 0xd0400000-0xd04fffff]
Jan 11 06:08:43 l05 kernel: [    1.365042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jan 11 06:08:43 l05 kernel: [    1.365218] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jan 11 06:08:43 l05 kernel: [    1.365252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Jan 11 06:08:43 l05 kernel: [    1.365298] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Jan 11 06:08:43 l05 kernel: [    1.365751]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Jan 11 06:08:43 l05 kernel: [    1.366924]  pci0000:00: ACPI _OSC control (0x1d) granted
Jan 11 06:08:43 l05 kernel: [    1.372380] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *10 11 12 14 15)
Jan 11 06:08:43 l05 kernel: [    1.372427] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 10 11 12 14 15)
Jan 11 06:08:43 l05 kernel: [    1.372470] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
Jan 11 06:08:43 l05 kernel: [    1.372512] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
Jan 11 06:08:43 l05 kernel: [    1.372554] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
Jan 11 06:08:43 l05 kernel: [    1.372595] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Jan 11 06:08:43 l05 kernel: [    1.372639] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *10 11 12 14 15)
Jan 11 06:08:43 l05 kernel: [    1.372681] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Jan 11 06:08:43 l05 kernel: [    1.372789] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jan 11 06:08:43 l05 kernel: [    1.372796] vgaarb: loaded
Jan 11 06:08:43 l05 kernel: [    1.372797] vgaarb: bridge control possible 0000:00:02.0
Jan 11 06:08:43 l05 kernel: [    1.372899] i2c-core: driver [aat2870] using legacy suspend method
Jan 11 06:08:43 l05 kernel: [    1.372901] i2c-core: driver [aat2870] using legacy resume method
Jan 11 06:08:43 l05 kernel: [    1.372959] SCSI subsystem initialized
Jan 11 06:08:43 l05 kernel: [    1.373015] libata version 3.00 loaded.
Jan 11 06:08:43 l05 kernel: [    1.373060] usbcore: registered new interface driver usbfs
Jan 11 06:08:43 l05 kernel: [    1.373070] usbcore: registered new interface driver hub
Jan 11 06:08:43 l05 kernel: [    1.373095] usbcore: registered new device driver usb
Jan 11 06:08:43 l05 kernel: [    1.373177] PCI: Using ACPI for IRQ routing
Jan 11 06:08:43 l05 kernel: [    1.380321] PCI: pci_cache_line_size set to 64 bytes
Jan 11 06:08:43 l05 kernel: [    1.380411] reserve RAM buffer: 000000000009dc00 - 000000000009ffff
Jan 11 06:08:43 l05 kernel: [    1.380413] reserve RAM buffer: 0000000040004000 - 0000000043ffffff
Jan 11 06:08:43 l05 kernel: [    1.380415] reserve RAM buffer: 00000000b8b9d000 - 00000000bbffffff
Jan 11 06:08:43 l05 kernel: [    1.380418] reserve RAM buffer: 00000000b9fb3000 - 00000000bbffffff
Jan 11 06:08:43 l05 kernel: [    1.380420] reserve RAM buffer: 00000000ba000000 - 00000000bbffffff
Jan 11 06:08:43 l05 kernel: [    1.380422] reserve RAM buffer: 000000023ee00000 - 000000023fffffff
Jan 11 06:08:43 l05 kernel: [    1.380522] NetLabel: Initializing
Jan 11 06:08:43 l05 kernel: [    1.380523] NetLabel:  domain hash size = 128
Jan 11 06:08:43 l05 kernel: [    1.380525] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 11 06:08:43 l05 kernel: [    1.380535] NetLabel:  unlabeled traffic allowed by default
Jan 11 06:08:43 l05 kernel: [    1.380588] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Jan 11 06:08:43 l05 kernel: [    1.380595] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Jan 11 06:08:43 l05 kernel: [    1.382611] Switching to clocksource hpet
Jan 11 06:08:43 l05 kernel: [    1.388502] AppArmor: AppArmor Filesystem Enabled
Jan 11 06:08:43 l05 kernel: [    1.388527] pnp: PnP ACPI init
Jan 11 06:08:43 l05 kernel: [    1.388538] ACPI: bus type pnp registered
Jan 11 06:08:43 l05 kernel: [    1.388887] pnp 00:00: [bus 00-3e]
Jan 11 06:08:43 l05 kernel: [    1.388890] pnp 00:00: [io  0x0000-0x0cf7 window]
Jan 11 06:08:43 l05 kernel: [    1.388892] pnp 00:00: [io  0x0cf8-0x0cff]
Jan 11 06:08:43 l05 kernel: [    1.388894] pnp 00:00: [io  0x0d00-0xffff window]
Jan 11 06:08:43 l05 kernel: [    1.388896] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Jan 11 06:08:43 l05 kernel: [    1.388898] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Jan 11 06:08:43 l05 kernel: [    1.388900] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Jan 11 06:08:43 l05 kernel: [    1.388902] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Jan 11 06:08:43 l05 kernel: [    1.388904] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Jan 11 06:08:43 l05 kernel: [    1.388906] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Jan 11 06:08:43 l05 kernel: [    1.388908] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Jan 11 06:08:43 l05 kernel: [    1.388910] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Jan 11 06:08:43 l05 kernel: [    1.388912] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Jan 11 06:08:43 l05 kernel: [    1.388914] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Jan 11 06:08:43 l05 kernel: [    1.388916] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Jan 11 06:08:43 l05 kernel: [    1.388918] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Jan 11 06:08:43 l05 kernel: [    1.388920] pnp 00:00: [mem 0x000ec000-0x000effff window]
Jan 11 06:08:43 l05 kernel: [    1.388922] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Jan 11 06:08:43 l05 kernel: [    1.388924] pnp 00:00: [mem 0xbf200000-0xdfffffff window]
Jan 11 06:08:43 l05 kernel: [    1.388927] pnp 00:00: [mem 0xf0000000-0xfedfffff window]
Jan 11 06:08:43 l05 kernel: [    1.388929] pnp 00:00: [mem 0xfee01000-0xffffffff window]
Jan 11 06:08:43 l05 kernel: [    1.388996] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Jan 11 06:08:43 l05 kernel: [    1.389089] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
Jan 11 06:08:43 l05 kernel: [    1.389091] pnp 00:01: [mem 0xfed10000-0xfed17fff]
Jan 11 06:08:43 l05 kernel: [    1.389093] pnp 00:01: [mem 0xfed18000-0xfed18fff]
Jan 11 06:08:43 l05 kernel: [    1.389095] pnp 00:01: [mem 0xfed19000-0xfed19fff]
Jan 11 06:08:43 l05 kernel: [    1.389097] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Jan 11 06:08:43 l05 kernel: [    1.389099] pnp 00:01: [mem 0xe0000000-0xefffffff]
Jan 11 06:08:43 l05 kernel: [    1.389101] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
Jan 11 06:08:43 l05 kernel: [    1.389103] pnp 00:01: [mem 0xfed90000-0xfed93fff]
Jan 11 06:08:43 l05 kernel: [    1.389104] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
Jan 11 06:08:43 l05 kernel: [    1.389106] pnp 00:01: [mem 0xfec00000-0xfec00fff]
Jan 11 06:08:43 l05 kernel: [    1.389149] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389152] system 00:01: [mem 0xfed10000-0xfed17fff] could not be reserved
Jan 11 06:08:43 l05 kernel: [    1.389155] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389157] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389160] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389162] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389165] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389167] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389170] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
Jan 11 06:08:43 l05 kernel: [    1.389173] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 11 06:08:43 l05 kernel: [    1.389266] pnp 00:02: [io  0x0000-0x001f]
Jan 11 06:08:43 l05 kernel: [    1.389268] pnp 00:02: [io  0x0081-0x0091]
Jan 11 06:08:43 l05 kernel: [    1.389270] pnp 00:02: [io  0x0093-0x009f]
Jan 11 06:08:43 l05 kernel: [    1.389272] pnp 00:02: [io  0x00c0-0x00df]
Jan 11 06:08:43 l05 kernel: [    1.389274] pnp 00:02: [dma 4]
Jan 11 06:08:43 l05 kernel: [    1.389309] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Jan 11 06:08:43 l05 kernel: [    1.389317] pnp 00:03: [mem 0xff000000-0xffffffff]
Jan 11 06:08:43 l05 kernel: [    1.389347] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
Jan 11 06:08:43 l05 kernel: [    1.389398] pnp 00:04: [io  0xfe00-0xfe0f]
Jan 11 06:08:43 l05 kernel: [    1.389400] pnp 00:04: [io  0xfe80-0xfe8f]
Jan 11 06:08:43 l05 kernel: [    1.389401] pnp 00:04: [mem 0xfed40000-0xfed44fff]
Jan 11 06:08:43 l05 kernel: [    1.389436] pnp 00:04: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
Jan 11 06:08:43 l05 kernel: [    1.389517] pnp 00:05: [mem 0xfed00000-0xfed003ff]
Jan 11 06:08:43 l05 kernel: [    1.389552] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
Jan 11 06:08:43 l05 kernel: [    1.389562] pnp 00:06: [io  0x00f0]
Jan 11 06:08:43 l05 kernel: [    1.389572] pnp 00:06: [irq 13]
Jan 11 06:08:43 l05 kernel: [    1.389603] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Jan 11 06:08:43 l05 kernel: [    1.389613] pnp 00:07: [io  0x002e-0x002f]
Jan 11 06:08:43 l05 kernel: [    1.389615] pnp 00:07: [io  0x004e-0x004f]
Jan 11 06:08:43 l05 kernel: [    1.389616] pnp 00:07: [io  0x0061]
Jan 11 06:08:43 l05 kernel: [    1.389618] pnp 00:07: [io  0x0063]
Jan 11 06:08:43 l05 kernel: [    1.389620] pnp 00:07: [io  0x0065]
Jan 11 06:08:43 l05 kernel: [    1.389621] pnp 00:07: [io  0x0067]
Jan 11 06:08:43 l05 kernel: [    1.389623] pnp 00:07: [io  0x0070]
Jan 11 06:08:43 l05 kernel: [    1.389624] pnp 00:07: [io  0x0080]
Jan 11 06:08:43 l05 kernel: [    1.389626] pnp 00:07: [io  0x0092]
Jan 11 06:08:43 l05 kernel: [    1.389627] pnp 00:07: [io  0x00b2-0x00b3]
Jan 11 06:08:43 l05 kernel: [    1.389629] pnp 00:07: [io  0x0200-0x027f]
Jan 11 06:08:43 l05 kernel: [    1.389631] pnp 00:07: [io  0x1000-0x100f]
Jan 11 06:08:43 l05 kernel: [    1.389632] pnp 00:07: [io  0xffff]
Jan 11 06:08:43 l05 kernel: [    1.389634] pnp 00:07: [io  0xffff]
Jan 11 06:08:43 l05 kernel: [    1.389636] pnp 00:07: [io  0x0400-0x047f]
Jan 11 06:08:43 l05 kernel: [    1.389637] pnp 00:07: [io  0x0500-0x057f]
Jan 11 06:08:43 l05 kernel: [    1.389639] pnp 00:07: [io  0xef80-0xef9f]
Jan 11 06:08:43 l05 kernel: [    1.389688] system 00:07: [io  0x0200-0x027f] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389691] system 00:07: [io  0x1000-0x100f] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389693] system 00:07: [io  0xffff] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389695] system 00:07: [io  0xffff] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389697] system 00:07: [io  0x0400-0x047f] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389699] system 00:07: [io  0x0500-0x057f] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389702] system 00:07: [io  0xef80-0xef9f] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.389705] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 11 06:08:43 l05 kernel: [    1.389713] pnp 00:08: [io  0x0070-0x0077]
Jan 11 06:08:43 l05 kernel: [    1.389720] pnp 00:08: [irq 8]
Jan 11 06:08:43 l05 kernel: [    1.389753] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan 11 06:08:43 l05 kernel: [    1.390120] pnp 00:09: [io  0x03f8-0x03ff]
Jan 11 06:08:43 l05 kernel: [    1.390126] pnp 00:09: [irq 4]
Jan 11 06:08:43 l05 kernel: [    1.390187] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)
Jan 11 06:08:43 l05 kernel: [    1.390519] pnp 00:0a: [io  0x0378-0x037f]
Jan 11 06:08:43 l05 kernel: [    1.390522] pnp 00:0a: [io  0x0778-0x077a]
Jan 11 06:08:43 l05 kernel: [    1.390527] pnp 00:0a: [irq 5]
Jan 11 06:08:43 l05 kernel: [    1.390529] pnp 00:0a: [dma 0 disabled]
Jan 11 06:08:43 l05 kernel: [    1.390634] pnp 00:0a: Plug and Play ACPI device, IDs PNP0401 (active)
Jan 11 06:08:43 l05 kernel: [    1.390643] pnp 00:0b: [io  0x0060]
Jan 11 06:08:43 l05 kernel: [    1.390645] pnp 00:0b: [io  0x0064]
Jan 11 06:08:43 l05 kernel: [    1.390650] pnp 00:0b: [irq 1]
Jan 11 06:08:43 l05 kernel: [    1.390687] pnp 00:0b: Plug and Play ACPI device, IDs HPQ8001 PNP0303 (active)
Jan 11 06:08:43 l05 kernel: [    1.390698] pnp 00:0c: [irq 12]
Jan 11 06:08:43 l05 kernel: [    1.390735] pnp 00:0c: Plug and Play ACPI device, IDs SYN0192 SYN0100 SYN0002 PNP0f13 (active)
Jan 11 06:08:43 l05 kernel: [    1.390952] pnp 00:0d: [irq 23]
Jan 11 06:08:43 l05 kernel: [    1.390996] pnp 00:0d: Plug and Play ACPI device, IDs HPQ6000 (active)
Jan 11 06:08:43 l05 kernel: [    1.391036] pnp 00:0e: [mem 0x20000000-0x201fffff]
Jan 11 06:08:43 l05 kernel: [    1.391038] pnp 00:0e: [mem 0x40004000-0x40004fff]
Jan 11 06:08:43 l05 kernel: [    1.391093] system 00:0e: [mem 0x20000000-0x201fffff] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.391095] system 00:0e: [mem 0x40004000-0x40004fff] has been reserved
Jan 11 06:08:43 l05 kernel: [    1.391098] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
Jan 11 06:08:43 l05 kernel: [    1.391282] pnp: PnP ACPI: found 15 devices
Jan 11 06:08:43 l05 kernel: [    1.391284] ACPI: ACPI bus type pnp unregistered
Jan 11 06:08:43 l05 kernel: [    1.397782] pci 0000:02:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
Jan 11 06:08:43 l05 kernel: [    1.397787] PCI: max bus depth: 1 pci_try_num: 2
Jan 11 06:08:43 l05 kernel: [    1.397823] pci 0000:00:1c.2: BAR 15: assigned [mem 0xbf200000-0xbf2fffff pref]
Jan 11 06:08:43 l05 kernel: [    1.397825] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
Jan 11 06:08:43 l05 kernel: [    1.397831] pci 0000:00:1c.0:   bridge window [mem 0xd0600000-0xd06fffff]
Jan 11 06:08:43 l05 kernel: [    1.397842] pci 0000:02:00.0: BAR 6: assigned [mem 0xbf200000-0xbf20ffff pref]
Jan 11 06:08:43 l05 kernel: [    1.397844] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
Jan 11 06:08:43 l05 kernel: [    1.397850] pci 0000:00:1c.2:   bridge window [mem 0xd0500000-0xd05fffff]
Jan 11 06:08:43 l05 kernel: [    1.397856] pci 0000:00:1c.2:   bridge window [mem 0xbf200000-0xbf2fffff pref]
Jan 11 06:08:43 l05 kernel: [    1.397863] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
Jan 11 06:08:43 l05 kernel: [    1.397869] pci 0000:00:1c.3:   bridge window [mem 0xd0400000-0xd04fffff]
Jan 11 06:08:43 l05 kernel: [    1.397891] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 11 06:08:43 l05 kernel: [    1.397898] pci 0000:00:1c.0: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    1.397909] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 11 06:08:43 l05 kernel: [    1.397914] pci 0000:00:1c.2: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    1.397924] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jan 11 06:08:43 l05 kernel: [    1.397929] pci 0000:00:1c.3: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    1.397934] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jan 11 06:08:43 l05 kernel: [    1.397936] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jan 11 06:08:43 l05 kernel: [    1.397938] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jan 11 06:08:43 l05 kernel: [    1.397940] pci_bus 0000:00: resource 7 [mem 0xbf200000-0xdfffffff]
Jan 11 06:08:43 l05 kernel: [    1.397942] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfedfffff]
Jan 11 06:08:43 l05 kernel: [    1.397944] pci_bus 0000:00: resource 9 [mem 0xfee01000-0xffffffff]
Jan 11 06:08:43 l05 kernel: [    1.397947] pci_bus 0000:01: resource 1 [mem 0xd0600000-0xd06fffff]
Jan 11 06:08:43 l05 kernel: [    1.397949] pci_bus 0000:02: resource 1 [mem 0xd0500000-0xd05fffff]
Jan 11 06:08:43 l05 kernel: [    1.397951] pci_bus 0000:02: resource 2 [mem 0xbf200000-0xbf2fffff pref]
Jan 11 06:08:43 l05 kernel: [    1.397954] pci_bus 0000:03: resource 1 [mem 0xd0400000-0xd04fffff]
Jan 11 06:08:43 l05 kernel: [    1.397982] NET: Registered protocol family 2
Jan 11 06:08:43 l05 kernel: [    1.398167] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jan 11 06:08:43 l05 kernel: [    1.398965] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jan 11 06:08:43 l05 kernel: [    1.400219] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jan 11 06:08:43 l05 kernel: [    1.400348] TCP: Hash tables configured (established 524288 bind 65536)
Jan 11 06:08:43 l05 kernel: [    1.400350] TCP reno registered
Jan 11 06:08:43 l05 kernel: [    1.400364] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Jan 11 06:08:43 l05 kernel: [    1.400401] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Jan 11 06:08:43 l05 kernel: [    1.400499] NET: Registered protocol family 1
Jan 11 06:08:43 l05 kernel: [    1.400514] pci 0000:00:02.0: Boot video device
Jan 11 06:08:43 l05 kernel: [    1.400523] pci 0000:00:14.0: enabling device (0000 -> 0002)
Jan 11 06:08:43 l05 kernel: [    1.400528] pci 0000:00:14.0: can't derive routing for PCI INT A
Jan 11 06:08:43 l05 kernel: [    1.400529] pci 0000:00:14.0: PCI INT A: no GSI - using ISA IRQ 10
Jan 11 06:08:43 l05 kernel: [    1.400607] pci 0000:00:14.0: can't derive routing for PCI INT A
Jan 11 06:08:43 l05 kernel: [    1.400630] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 11 06:08:43 l05 kernel: [    1.400666] pci 0000:00:1a.0: PCI INT A disabled
Jan 11 06:08:43 l05 kernel: [    1.400686] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 11 06:08:43 l05 kernel: [    1.400712] pci 0000:00:1d.0: PCI INT A disabled
Jan 11 06:08:43 l05 kernel: [    1.400733] PCI: CLS 64 bytes, default 64
Jan 11 06:08:43 l05 kernel: [    1.400735] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jan 11 06:08:43 l05 kernel: [    1.400737] Placing 64MB software IO TLB between ffff8800b4b9d000 - ffff8800b8b9d000
Jan 11 06:08:43 l05 kernel: [    1.400739] software IO TLB at phys 0xb4b9d000 - 0xb8b9d000
Jan 11 06:08:43 l05 kernel: [    1.401239] audit: initializing netlink socket (disabled)
Jan 11 06:08:43 l05 kernel: [    1.401253] type=2000 audit(1389380913.184:1): initialized
Jan 11 06:08:43 l05 kernel: [    1.426910] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan 11 06:08:43 l05 kernel: [    1.428962] VFS: Disk quotas dquot_6.5.2
Jan 11 06:08:43 l05 kernel: [    1.429013] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jan 11 06:08:43 l05 kernel: [    1.429466] fuse init (API version 7.17)
Jan 11 06:08:43 l05 kernel: [    1.429553] msgmni has been set to 15697
Jan 11 06:08:43 l05 kernel: [    1.429922] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jan 11 06:08:43 l05 kernel: [    1.429950] io scheduler noop registered
Jan 11 06:08:43 l05 kernel: [    1.429952] io scheduler deadline registered
Jan 11 06:08:43 l05 kernel: [    1.429982] io scheduler cfq registered (default)
Jan 11 06:08:43 l05 kernel: [    1.430073] pcieport 0000:00:1c.0: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    1.430126] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [    1.430203] pcieport 0000:00:1c.2: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    1.430248] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [    1.430323] pcieport 0000:00:1c.3: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    1.430368] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [    1.430461] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
Jan 11 06:08:43 l05 kernel: [    1.430466] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
Jan 11 06:08:43 l05 kernel: [    1.430485] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
Jan 11 06:08:43 l05 kernel: [    1.430500] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Jan 11 06:08:43 l05 kernel: [    1.430503] pci 0000:02:00.2: Signaling PME through PCIe PME interrupt
Jan 11 06:08:43 l05 kernel: [    1.430507] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
Jan 11 06:08:43 l05 kernel: [    1.430526] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
Jan 11 06:08:43 l05 kernel: [    1.430528] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Jan 11 06:08:43 l05 kernel: [    1.430533] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
Jan 11 06:08:43 l05 kernel: [    1.430548] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 11 06:08:43 l05 kernel: [    1.430568] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan 11 06:08:43 l05 kernel: [    1.430616] intel_idle: MWAIT substates: 0x21120
Jan 11 06:08:43 l05 kernel: [    1.430618] intel_idle: v0.4 model 0x3A
Jan 11 06:08:43 l05 kernel: [    1.430619] intel_idle: lapic_timer_reliable_states 0xffffffff
Jan 11 06:08:43 l05 kernel: [    1.430759] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jan 11 06:08:43 l05 kernel: [    1.430857] ACPI: AC Adapter [AC] (on-line)
Jan 11 06:08:43 l05 kernel: [    1.431061] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Jan 11 06:08:43 l05 kernel: [    1.431066] ACPI: Sleep Button [SLPB]
Jan 11 06:08:43 l05 kernel: [    1.431104] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Jan 11 06:08:43 l05 kernel: [    1.431128] ACPI: Lid Switch [LID]
Jan 11 06:08:43 l05 kernel: [    1.431165] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jan 11 06:08:43 l05 kernel: [    1.431169] ACPI: Power Button [PWRF]
Jan 11 06:08:43 l05 kernel: [    1.453513] thermal LNXTHERM:00: registered as thermal_zone0
Jan 11 06:08:43 l05 kernel: [    1.453516] ACPI: Thermal Zone [CPUZ] (44 C)
Jan 11 06:08:43 l05 kernel: [    1.472458] thermal LNXTHERM:01: registered as thermal_zone1
Jan 11 06:08:43 l05 kernel: [    1.472460] ACPI: Thermal Zone [GFXZ] (0 C)
Jan 11 06:08:43 l05 kernel: [    1.482381] thermal LNXTHERM:02: registered as thermal_zone2
Jan 11 06:08:43 l05 kernel: [    1.482384] ACPI: Thermal Zone [EXTZ] (49 C)
Jan 11 06:08:43 l05 kernel: [    1.492339] thermal LNXTHERM:03: registered as thermal_zone3
Jan 11 06:08:43 l05 kernel: [    1.492341] ACPI: Thermal Zone [LOCZ] (27 C)
Jan 11 06:08:43 l05 kernel: [    1.502315] thermal LNXTHERM:04: registered as thermal_zone4
Jan 11 06:08:43 l05 kernel: [    1.502317] ACPI: Thermal Zone [BATZ] (26 C)
Jan 11 06:08:43 l05 kernel: [    1.502601] thermal LNXTHERM:05: registered as thermal_zone5
Jan 11 06:08:43 l05 kernel: [    1.502603] ACPI: Thermal Zone [PCHZ] (127 C)
Jan 11 06:08:43 l05 kernel: [    1.502680] thermal LNXTHERM:06: registered as thermal_zone6
Jan 11 06:08:43 l05 kernel: [    1.502682] ACPI: Thermal Zone [DM1Z] (0 C)
Jan 11 06:08:43 l05 kernel: [    1.502755] thermal LNXTHERM:07: registered as thermal_zone7
Jan 11 06:08:43 l05 kernel: [    1.502756] ACPI: Thermal Zone [DM2Z] (0 C)
Jan 11 06:08:43 l05 kernel: [    1.502781] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Jan 11 06:08:43 l05 kernel: [    1.502788] ACPI: Battery Slot [BAT0] (battery present)
Jan 11 06:08:43 l05 kernel: [    1.502813] ERST: Table is not found!
Jan 11 06:08:43 l05 kernel: [    1.502814] GHES: HEST is not enabled!
Jan 11 06:08:43 l05 kernel: [    1.502893] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jan 11 06:08:43 l05 kernel: [    1.523587] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 11 06:08:43 l05 kernel: [    1.546316] ACPI: Battery Slot [BAT0] (battery present)
Jan 11 06:08:43 l05 kernel: [    1.671181] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan 11 06:08:43 l05 kernel: [    1.671296] serial 0000:00:16.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan 11 06:08:43 l05 kernel: [    1.691546] 0000:00:16.3: ttyS4 at I/O 0x2090 (irq = 17) is a 16550A
Jan 11 06:08:43 l05 kernel: [    1.706407] Linux agpgart interface v0.103
Jan 11 06:08:43 l05 kernel: [    1.706491] agpgart-intel 0000:00:00.0: Intel Ivybridge Chipset
Jan 11 06:08:43 l05 kernel: [    1.706645] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
Jan 11 06:08:43 l05 kernel: [    1.708325] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
Jan 11 06:08:43 l05 kernel: [    1.708442] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Jan 11 06:08:43 l05 kernel: [    1.709687] brd: module loaded
Jan 11 06:08:43 l05 kernel: [    1.710362] loop: module loaded
Jan 11 06:08:43 l05 kernel: [    1.710480] ahci 0000:00:1f.2: version 3.0
Jan 11 06:08:43 l05 kernel: [    1.710493] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 11 06:08:43 l05 kernel: [    1.710542] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [    1.710570] ahci: SSS flag set, parallel bus scan disabled
Jan 11 06:08:43 l05 kernel: [    1.726163] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x29 impl SATA mode
Jan 11 06:08:43 l05 kernel: [    1.726166] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst
Jan 11 06:08:43 l05 kernel: [    1.726173] ahci 0000:00:1f.2: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    1.742549] scsi0 : ahci
Jan 11 06:08:43 l05 kernel: [    1.742638] scsi1 : ahci
Jan 11 06:08:43 l05 kernel: [    1.742706] scsi2 : ahci
Jan 11 06:08:43 l05 kernel: [    1.742775] scsi3 : ahci
Jan 11 06:08:43 l05 kernel: [    1.742843] scsi4 : ahci
Jan 11 06:08:43 l05 kernel: [    1.742908] scsi5 : ahci
Jan 11 06:08:43 l05 kernel: [    1.743144] ata1: SATA max UDMA/133 abar m2048@0xd0737000 port 0xd0737100 irq 43
Jan 11 06:08:43 l05 kernel: [    1.743146] ata2: DUMMY
Jan 11 06:08:43 l05 kernel: [    1.743147] ata3: DUMMY
Jan 11 06:08:43 l05 kernel: [    1.743151] ata4: SATA max UDMA/133 abar m2048@0xd0737000 port 0xd0737280 irq 43
Jan 11 06:08:43 l05 kernel: [    1.743152] ata5: DUMMY
Jan 11 06:08:43 l05 kernel: [    1.743155] ata6: SATA max UDMA/133 abar m2048@0xd0737000 port 0xd0737380 irq 43
Jan 11 06:08:43 l05 kernel: [    1.743480] Fixed MDIO Bus: probed
Jan 11 06:08:43 l05 kernel: [    1.743498] tun: Universal TUN/TAP device driver, 1.6
Jan 11 06:08:43 l05 kernel: [    1.743499] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan 11 06:08:43 l05 kernel: [    1.743543] PPP generic driver version 2.4.2
Jan 11 06:08:43 l05 kernel: [    1.743632] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan 11 06:08:43 l05 kernel: [    1.743648] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 11 06:08:43 l05 kernel: [    1.743667] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    1.743671] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Jan 11 06:08:43 l05 kernel: [    1.743712] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jan 11 06:08:43 l05 kernel: [    1.743743] ehci_hcd 0000:00:1a.0: debug port 2
Jan 11 06:08:43 l05 kernel: [    1.747627] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Jan 11 06:08:43 l05 kernel: [    1.747643] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xd0739000
Jan 11 06:08:43 l05 kernel: [    1.762098] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Jan 11 06:08:43 l05 kernel: [    1.762214] hub 1-0:1.0: USB hub found
Jan 11 06:08:43 l05 kernel: [    1.762218] hub 1-0:1.0: 3 ports detected
Jan 11 06:08:43 l05 kernel: [    1.762278] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 11 06:08:43 l05 kernel: [    1.762294] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    1.762298] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Jan 11 06:08:43 l05 kernel: [    1.762341] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan 11 06:08:43 l05 kernel: [    1.762363] ehci_hcd 0000:00:1d.0: debug port 2
Jan 11 06:08:43 l05 kernel: [    1.766248] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Jan 11 06:08:43 l05 kernel: [    1.766253] ehci_hcd 0000:00:1d.0: irq 16, io mem 0xd0738000
Jan 11 06:08:43 l05 kernel: [    1.782073] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Jan 11 06:08:43 l05 kernel: [    1.782177] hub 2-0:1.0: USB hub found
Jan 11 06:08:43 l05 kernel: [    1.782181] hub 2-0:1.0: 3 ports detected
Jan 11 06:08:43 l05 kernel: [    1.782236] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 11 06:08:43 l05 kernel: [    1.782246] uhci_hcd: USB Universal Host Controller Interface driver
Jan 11 06:08:43 l05 kernel: [    1.782271] xhci_hcd 0000:00:14.0: can't derive routing for PCI INT A
Jan 11 06:08:43 l05 kernel: [    1.782273] xhci_hcd 0000:00:14.0: PCI INT A: no GSI - using ISA IRQ 10
Jan 11 06:08:43 l05 kernel: [    1.782305] xhci_hcd 0000:00:14.0: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    1.782309] xhci_hcd 0000:00:14.0: xHCI Host Controller
Jan 11 06:08:43 l05 kernel: [    1.782349] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
Jan 11 06:08:43 l05 kernel: [    1.782439] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Jan 11 06:08:43 l05 kernel: [    1.782484] xhci_hcd 0000:00:14.0: irq 44 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [    1.782590] xHCI xhci_add_endpoint called for root hub
Jan 11 06:08:43 l05 kernel: [    1.782592] xHCI xhci_check_bandwidth called for root hub
Jan 11 06:08:43 l05 kernel: [    1.782613] hub 3-0:1.0: USB hub found
Jan 11 06:08:43 l05 kernel: [    1.782621] hub 3-0:1.0: 4 ports detected
Jan 11 06:08:43 l05 kernel: [    1.782673] xhci_hcd 0000:00:14.0: xHCI Host Controller
Jan 11 06:08:43 l05 kernel: [    1.782708] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
Jan 11 06:08:43 l05 kernel: [    1.782782] xHCI xhci_add_endpoint called for root hub
Jan 11 06:08:43 l05 kernel: [    1.782784] xHCI xhci_check_bandwidth called for root hub
Jan 11 06:08:43 l05 kernel: [    1.782805] hub 4-0:1.0: USB hub found
Jan 11 06:08:43 l05 kernel: [    1.782812] hub 4-0:1.0: 4 ports detected
Jan 11 06:08:43 l05 kernel: [    1.850018] usbcore: registered new interface driver libusual
Jan 11 06:08:43 l05 kernel: [    1.850059] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 11 06:08:43 l05 kernel: [    1.851842] i8042: Detected active multiplexing controller, rev 1.1
Jan 11 06:08:43 l05 kernel: [    1.852611] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 11 06:08:43 l05 kernel: [    1.852617] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan 11 06:08:43 l05 kernel: [    1.852643] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan 11 06:08:43 l05 kernel: [    1.852663] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan 11 06:08:43 l05 kernel: [    1.852683] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan 11 06:08:43 l05 kernel: [    1.852784] mousedev: PS/2 mouse device common for all mice
Jan 11 06:08:43 l05 kernel: [    1.852942] rtc_cmos 00:08: RTC can wake from S4
Jan 11 06:08:43 l05 kernel: [    1.853050] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Jan 11 06:08:43 l05 kernel: [    1.853078] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Jan 11 06:08:43 l05 kernel: [    1.853155] device-mapper: uevent: version 1.0.3
Jan 11 06:08:43 l05 kernel: [    1.853221] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
Jan 11 06:08:43 l05 kernel: [    1.853339] cpuidle: using governor ladder
Jan 11 06:08:43 l05 kernel: [    1.853508] cpuidle: using governor menu
Jan 11 06:08:43 l05 kernel: [    1.853510] EFI Variables Facility v0.08 2004-May-17
Jan 11 06:08:43 l05 kernel: [    1.853702] TCP cubic registered
Jan 11 06:08:43 l05 kernel: [    1.853807] NET: Registered protocol family 10
Jan 11 06:08:43 l05 kernel: [    1.854200] NET: Registered protocol family 17
Jan 11 06:08:43 l05 kernel: [    1.854204] Registering the dns_resolver key type
Jan 11 06:08:43 l05 kernel: [    1.854334] PM: Hibernation image not present or could not be loaded.
Jan 11 06:08:43 l05 kernel: [    1.854344] registered taskstats version 1
Jan 11 06:08:43 l05 kernel: [    1.861642]   Magic number: 14:798:141
Jan 11 06:08:43 l05 kernel: [    1.861656] block ram6: hash matches
Jan 11 06:08:43 l05 kernel: [    1.861696] acpi device:12: hash matches
Jan 11 06:08:43 l05 kernel: [    1.861755] rtc_cmos 00:08: setting system clock to 2014-01-10 19:08:34 UTC (1389380914)
Jan 11 06:08:43 l05 kernel: [    1.862448] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 11 06:08:43 l05 kernel: [    1.862450] EDD information not available.
Jan 11 06:08:43 l05 kernel: [    1.873626] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jan 11 06:08:43 l05 kernel: [    1.993882] usb 4-1: new SuperSpeed USB device number 2 using xhci_hcd
Jan 11 06:08:43 l05 kernel: [    2.010748] hub 4-1:1.0: USB hub found
Jan 11 06:08:43 l05 kernel: [    2.010779] hub 4-1:1.0: 4 ports detected
Jan 11 06:08:43 l05 kernel: [    2.061741] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jan 11 06:08:43 l05 kernel: [    2.062196] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Jan 11 06:08:43 l05 kernel: [    2.062199] ata1.00: supports DRM functions and may not be fully accessible
Jan 11 06:08:43 l05 kernel: [    2.062292] ata1.00: ATA-9: MTFDDAK256MAM-1K12, 07TA, max UDMA/100
Jan 11 06:08:43 l05 kernel: [    2.062301] ata1.00: 500118192 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
Jan 11 06:08:43 l05 kernel: [    2.062857] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Jan 11 06:08:43 l05 kernel: [    2.062876] ata1.00: supports DRM functions and may not be fully accessible
Jan 11 06:08:43 l05 kernel: [    2.062972] ata1.00: configured for UDMA/100
Jan 11 06:08:43 l05 kernel: [    2.069965] scsi 0:0:0:0: Direct-Access     ATA      MTFDDAK256MAM-1K 07TA PQ: 0 ANSI: 5
Jan 11 06:08:43 l05 kernel: [    2.070080] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 11 06:08:43 l05 kernel: [    2.070116] sd 0:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
Jan 11 06:08:43 l05 kernel: [    2.070284] sd 0:0:0:0: [sda] Write Protect is off
Jan 11 06:08:43 l05 kernel: [    2.070299] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 11 06:08:43 l05 kernel: [    2.070459] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 11 06:08:43 l05 kernel: [    2.071932]  sda: sda1 sda3 < sda5 >
Jan 11 06:08:43 l05 kernel: [    2.072494] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 11 06:08:43 l05 kernel: [    2.121663] usb 1-1: new high-speed USB device number 2 using ehci_hcd
Jan 11 06:08:43 l05 kernel: [    2.254285] hub 1-1:1.0: USB hub found
Jan 11 06:08:43 l05 kernel: [    2.254475] hub 1-1:1.0: 6 ports detected
Jan 11 06:08:43 l05 kernel: [    2.365335] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Jan 11 06:08:43 l05 kernel: [    2.389315] ata4: SATA link down (SStatus 0 SControl 300)
Jan 11 06:08:43 l05 kernel: [    2.397298] Refined TSC clocksource calibration: 2494.333 MHz.
Jan 11 06:08:43 l05 kernel: [    2.397309] Switching to clocksource tsc
Jan 11 06:08:43 l05 kernel: [    2.497836] hub 2-1:1.0: USB hub found
Jan 11 06:08:43 l05 kernel: [    2.498028] hub 2-1:1.0: 8 ports detected
Jan 11 06:08:43 l05 kernel: [    2.664944] usb 3-1: new high-speed USB device number 2 using xhci_hcd
Jan 11 06:08:43 l05 kernel: [    2.681540] hub 3-1:1.0: USB hub found
Jan 11 06:08:43 l05 kernel: [    2.681564] hub 3-1:1.0: 4 ports detected
Jan 11 06:08:43 l05 kernel: [    2.708890] ata6: SATA link down (SStatus 0 SControl 300)
Jan 11 06:08:43 l05 kernel: [    2.709900] Freeing unused kernel memory: 924k freed
Jan 11 06:08:43 l05 kernel: [    2.709978] Write protecting the kernel read-only data: 12288k
Jan 11 06:08:43 l05 kernel: [    2.713055] Freeing unused kernel memory: 1584k freed
Jan 11 06:08:43 l05 kernel: [    2.715395] Freeing unused kernel memory: 1188k freed
Jan 11 06:08:43 l05 kernel: [    2.743993] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
Jan 11 06:08:43 l05 kernel: [    2.743995] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
Jan 11 06:08:43 l05 kernel: [    2.744017] e1000e 0000:00:19.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 11 06:08:43 l05 kernel: [    2.744026] e1000e 0000:00:19.0: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    2.744933] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [    2.745035] [drm] Initialized drm 1.1.0 20060810
Jan 11 06:08:43 l05 kernel: [    2.751084] wmi: Mapper loaded
Jan 11 06:08:43 l05 kernel: [    2.761656] sdhci: Secure Digital Host Controller Interface driver
Jan 11 06:08:43 l05 kernel: [    2.761659] sdhci: Copyright(c) Pierre Ossman
Jan 11 06:08:43 l05 kernel: [    2.761911] sdhci-pci 0000:02:00.0: SDHCI controller found [197b:2392] (rev 30)
Jan 11 06:08:43 l05 kernel: [    2.761931] sdhci-pci 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 11 06:08:43 l05 kernel: [    2.761973] sdhci-pci 0000:02:00.0: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    2.761995] mmc0: no vmmc regulator found
Jan 11 06:08:43 l05 kernel: [    2.762027] Registered led device: mmc0::
Jan 11 06:08:43 l05 kernel: [    2.763063] mmc0: SDHCI controller on PCI [0000:02:00.0] using DMA
Jan 11 06:08:43 l05 kernel: [    2.763081] sdhci-pci 0000:02:00.2: SDHCI controller found [197b:2391] (rev 30)
Jan 11 06:08:43 l05 kernel: [    2.763099] sdhci-pci 0000:02:00.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 11 06:08:43 l05 kernel: [    2.763105] sdhci-pci 0000:02:00.2: Refusing to bind to secondary interface.
Jan 11 06:08:43 l05 kernel: [    2.763113] sdhci-pci 0000:02:00.2: PCI INT A disabled
Jan 11 06:08:43 l05 kernel: [    2.848719] usb 3-2: new full-speed USB device number 3 using xhci_hcd
Jan 11 06:08:43 l05 kernel: [    2.873693] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input4
Jan 11 06:08:43 l05 kernel: [    2.873848] generic-usb 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:14.0-2/input0
Jan 11 06:08:43 l05 kernel: [    2.879245] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.1/input/input5
Jan 11 06:08:43 l05 kernel: [    2.879388] generic-usb 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:14.0-2/input1
Jan 11 06:08:43 l05 kernel: [    2.893874] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.2/input/input6
Jan 11 06:08:43 l05 kernel: [    2.893994] generic-usb 0003:045E:0745.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:14.0-2/input2
Jan 11 06:08:43 l05 kernel: [    2.894008] usbcore: registered new interface driver usbhid
Jan 11 06:08:43 l05 kernel: [    2.894009] usbhid: USB HID core driver
Jan 11 06:08:43 l05 kernel: [    2.940644] usb 1-1.1: new full-speed USB device number 3 using ehci_hcd
Jan 11 06:08:43 l05 kernel: [    2.942170] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 10:1f:74:77:1b:e1
Jan 11 06:08:43 l05 kernel: [    2.942173] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Jan 11 06:08:43 l05 kernel: [    2.942219] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
Jan 11 06:08:43 l05 kernel: [    2.942278] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 11 06:08:43 l05 kernel: [    2.942283] i915 0000:00:02.0: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [    2.992693] i915 0000:00:02.0: irq 46 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [    2.992697] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jan 11 06:08:43 l05 kernel: [    2.992698] [drm] Driver supports precise vblank timestamp query.
Jan 11 06:08:43 l05 kernel: [    2.992744] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
Jan 11 06:08:43 l05 kernel: [    2.993261] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jan 11 06:08:43 l05 kernel: [    3.033496] mmc0: new SDHC card at address e624
Jan 11 06:08:43 l05 kernel: [    3.034780] mmcblk0: mmc0:e624 SU32G 29.7 GiB
Jan 11 06:08:43 l05 kernel: [    3.039924]  mmcblk0: p1
Jan 11 06:08:43 l05 kernel: [    3.116432] usb 1-1.2: new full-speed USB device number 4 using ehci_hcd
Jan 11 06:08:43 l05 kernel: [    3.284405] usb 1-1.3: new high-speed USB device number 5 using ehci_hcd
Jan 11 06:08:43 l05 kernel: [    3.653613] fbcon: inteldrmfb (fb0) is primary device
Jan 11 06:08:43 l05 kernel: [    3.653655] Console: switching to colour frame buffer device 170x48
Jan 11 06:08:43 l05 kernel: [    3.653675] fb0: inteldrmfb frame buffer device
Jan 11 06:08:43 l05 kernel: [    3.653677] drm: registered panic notifier
Jan 11 06:08:43 l05 kernel: [    3.709740] acpi device:0b: registered as cooling_device4
Jan 11 06:08:43 l05 kernel: [    3.709995] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
Jan 11 06:08:43 l05 kernel: [    3.710042] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jan 11 06:08:43 l05 kernel: [    3.710092] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jan 11 06:08:43 l05 kernel: [    3.747787] usb 1-1.5: new high-speed USB device number 6 using ehci_hcd
Jan 11 06:08:43 l05 kernel: [    3.889239] [drm] Changing LVDS panel from (+hsync, +vsync) to (+hsync, -vsync)
Jan 11 06:08:43 l05 kernel: [    3.947381] usb 3-1.4: new low-speed USB device number 4 using xhci_hcd
Jan 11 06:08:43 l05 kernel: [    3.967295] usb 3-1.4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Jan 11 06:08:43 l05 kernel: [    3.967301] usb 3-1.4: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
Jan 11 06:08:43 l05 kernel: [    3.970096] input: HID 1017:0002 as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.4/3-1.4:1.0/input/input8
Jan 11 06:08:43 l05 kernel: [    3.970216] generic-usb 0003:1017:0002.0004: input,hidraw3: USB HID v1.00 Keyboard [HID 1017:0002] on usb-0000:00:14.0-1.4/input0
Jan 11 06:08:43 l05 kernel: [    3.974927] input: HID 1017:0002 as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.4/3-1.4:1.1/input/input9
Jan 11 06:08:43 l05 kernel: [    3.975125] generic-usb 0003:1017:0002.0005: input,hidraw4: USB HID v1.00 Mouse [HID 1017:0002] on usb-0000:00:14.0-1.4/input1
Jan 11 06:08:43 l05 kernel: [    9.891276] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan 11 06:08:43 l05 kernel: [   10.167654] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 11 06:08:43 l05 kernel: [   10.182873] lp: driver loaded but no devices found
Jan 11 06:08:43 l05 kernel: [   10.259015] mei: module is from the staging directory, the quality is unknown, you have been warned.
Jan 11 06:08:43 l05 kernel: [   10.259353] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 11 06:08:43 l05 kernel: [   10.259360] mei 0000:00:16.0: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [   10.259420] mei 0000:00:16.0: irq 47 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [   10.275105] hp_accel: laptop model unknown, using default axes configuration
Jan 11 06:08:43 l05 kernel: [   10.275671] lis3lv02d: 8 bits 3DC sensor found
Jan 11 06:08:43 l05 kernel: [   10.311483] tpm_tis 00:04: 1.2 TPM (device-id 0xB, rev-id 16)
Jan 11 06:08:43 l05 kernel: [   10.326674] type=1400 audit(1389380922.970:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=706 comm="apparmor_parser"
Jan 11 06:08:43 l05 kernel: [   10.326986] type=1400 audit(1389380922.974:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=706 comm="apparmor_parser"
Jan 11 06:08:43 l05 kernel: [   10.327164] type=1400 audit(1389380922.974:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=706 comm="apparmor_parser"
Jan 11 06:08:43 l05 kernel: [   10.335066] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input10
Jan 11 06:08:43 l05 kernel: [   10.335219] Registered led device: hp::hddprotect
Jan 11 06:08:43 l05 kernel: [   10.335248] hp_accel: driver loaded
Jan 11 06:08:43 l05 kernel: [   10.344096] cfg80211: Calling CRDA to update world regulatory domain
Jan 11 06:08:43 l05 kernel: [   10.351850] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Jan 11 06:08:43 l05 kernel: [   10.351853] Copyright(c) 2003-2011 Intel Corporation
Jan 11 06:08:43 l05 kernel: [   10.351896] iwlwifi 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jan 11 06:08:43 l05 kernel: [   10.351905] iwlwifi 0000:03:00.0: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [   10.351929] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
Jan 11 06:08:43 l05 kernel: [   10.351931] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900117f4000
Jan 11 06:08:43 l05 kernel: [   10.351933] iwlwifi 0000:03:00.0: HW Revision ID = 0x24
Jan 11 06:08:43 l05 kernel: [   10.352020] iwlwifi 0000:03:00.0: irq 48 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [   10.352057] iwlwifi 0000:03:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
Jan 11 06:08:43 l05 kernel: [   10.352126] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
Jan 11 06:08:43 l05 kernel: [   10.357676] Bluetooth: Core ver 2.16
Jan 11 06:08:43 l05 kernel: [   10.357692] NET: Registered protocol family 31
Jan 11 06:08:43 l05 kernel: [   10.357694] Bluetooth: HCI device and connection manager initialized
Jan 11 06:08:43 l05 kernel: [   10.357696] Bluetooth: HCI socket layer initialized
Jan 11 06:08:43 l05 kernel: [   10.357697] Bluetooth: L2CAP socket layer initialized
Jan 11 06:08:43 l05 kernel: [   10.357703] Bluetooth: SCO socket layer initialized
Jan 11 06:08:43 l05 kernel: [   10.357950] Bluetooth: Generic Bluetooth USB driver ver 0.6
Jan 11 06:08:43 l05 kernel: [   10.358764] usbcore: registered new interface driver btusb
Jan 11 06:08:43 l05 kernel: [   10.367573] iwlwifi 0000:03:00.0: device EEPROM VER=0x756, CALIB=0x6
Jan 11 06:08:43 l05 kernel: [   10.367576] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
Jan 11 06:08:43 l05 kernel: [   10.367579] iwlwifi 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Jan 11 06:08:43 l05 kernel: [   10.367603] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Jan 11 06:08:43 l05 kernel: [   10.382297] cdc_acm 1-1.5:1.1: ttyACM0: USB ACM device
Jan 11 06:08:43 l05 kernel: [   10.383849] cdc_acm 1-1.5:1.3: ttyACM1: USB ACM device
Jan 11 06:08:43 l05 kernel: [   10.392122] cdc_wdm 1-1.5:1.5: cdc-wdm0: USB WDM device
Jan 11 06:08:43 l05 kernel: [   10.392159] cdc_wdm 1-1.5:1.8: cdc-wdm1: USB WDM device
Jan 11 06:08:43 l05 kernel: [   10.392178] usbcore: registered new interface driver cdc_wdm
Jan 11 06:08:43 l05 kernel: [   10.392783] cdc_acm 1-1.5:1.9: ttyACM2: USB ACM device
Jan 11 06:08:43 l05 kernel: [   10.395234] Linux video capture interface: v2.00
Jan 11 06:08:43 l05 kernel: [   10.396100] uvcvideo: Found UVC 1.00 device HP HD Webcam [Fixed] (05c8:0340)
Jan 11 06:08:43 l05 kernel: [   10.396571] cdc_ncm: 04-Aug-2011
Jan 11 06:08:43 l05 kernel: [   10.399776] usbcore: registered new interface driver cdc_acm
Jan 11 06:08:43 l05 kernel: [   10.399778] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
Jan 11 06:08:43 l05 kernel: [   10.415537] input: HP HD Webcam [Fixed] as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input11
Jan 11 06:08:43 l05 kernel: [   10.415651] usbcore: registered new interface driver uvcvideo
Jan 11 06:08:43 l05 kernel: [   10.415654] USB Video Class driver (1.1.1)
Jan 11 06:08:43 l05 kernel: [   10.420041] usb 1-1.5: MAC-Address: 0x02:0x15:0xe0:0xec:0x01:0x00
Jan 11 06:08:43 l05 kernel: [   10.420673] cdc_ncm 1-1.5:1.6: usb0: register 'cdc_ncm' at usb-0000:00:1a.0-1.5, CDC NCM, 02:15:e0:ec:01:00
Jan 11 06:08:43 l05 kernel: [   10.420713] usbcore: registered new interface driver cdc_ncm
Jan 11 06:08:43 l05 kernel: [   10.438462] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
Jan 11 06:08:43 l05 kernel: [   10.438470] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
Jan 11 06:08:43 l05 kernel: [   10.438486] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jan 11 06:08:43 l05 kernel: [   10.438553] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [   10.438580] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
Jan 11 06:08:43 l05 kernel: [   10.487181] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
Jan 11 06:08:43 l05 kernel: [   10.487375] Registered led device: phy0-led
Jan 11 06:08:43 l05 kernel: [   10.487413] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jan 11 06:08:43 l05 kernel: [   10.492049] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Jan 11 06:08:43 l05 kernel: [   10.494656] ppdev: user-space parallel port driver
Jan 11 06:08:43 l05 kernel: [   10.502314] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jan 11 06:08:43 l05 kernel: [   10.502317] cfg80211: World regulatory domain updated:
Jan 11 06:08:43 l05 kernel: [   10.502319] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan 11 06:08:43 l05 kernel: [   10.502322] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 11 06:08:43 l05 kernel: [   10.502324] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 11 06:08:43 l05 kernel: [   10.502326] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 11 06:08:43 l05 kernel: [   10.502329] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 11 06:08:43 l05 kernel: [   10.502331] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 11 06:08:43 l05 kernel: [   10.610825] input: HP WMI hotkeys as /devices/virtual/input/input12
Jan 11 06:08:43 l05 kernel: [   10.730962] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Jan 11 06:08:43 l05 kernel: [   10.890004] RPC: Registered named UNIX socket transport module.
Jan 11 06:08:43 l05 kernel: [   10.890007] RPC: Registered udp transport module.
Jan 11 06:08:43 l05 kernel: [   10.890008] RPC: Registered tcp transport module.
Jan 11 06:08:43 l05 kernel: [   10.890009] RPC: Registered tcp NFSv4.1 backchannel transport module.
Jan 11 06:08:43 l05 kernel: [   10.892462] FS-Cache: Loaded
Jan 11 06:08:43 l05 kernel: [   10.897517] FS-Cache: Netfs 'nfs' registered for caching
Jan 11 06:08:43 l05 kernel: [   10.901750] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Jan 11 06:08:43 l05 kernel: [   10.910115] init: failsafe main process (1141) killed by TERM signal
Jan 11 06:08:43 l05 kernel: [   10.961351] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan 11 06:08:43 l05 kernel: [   10.961354] Bluetooth: BNEP filters: protocol multicast
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> DNS: loaded plugin dnsmasq
Jan 11 06:08:43 l05 sm-notify[1124]: Version 1.2.5 starting
Jan 11 06:08:43 l05 dbus[1167]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jan 11 06:08:43 l05 rpc.statd[1294]: Version 1.2.5 starting
Jan 11 06:08:43 l05 rpc.statd[1294]: Flags: TI-RPC
Jan 11 06:08:43 l05 modem-manager[1222]: <info>  (ttyS4) opening serial port...
Jan 11 06:08:43 l05 modem-manager[1222]: <info>  (ttyACM0) opening serial port...
Jan 11 06:08:43 l05 kernel: [   10.987208] Bluetooth: RFCOMM TTY layer initialized
Jan 11 06:08:43 l05 kernel: [   10.987213] Bluetooth: RFCOMM socket layer initialized
Jan 11 06:08:43 l05 kernel: [   10.987215] Bluetooth: RFCOMM ver 1.11
Jan 11 06:08:43 l05 polkitd[1285]: started daemon version 0.104 using authority implementation `local' version `0.104'
Jan 11 06:08:43 l05 modem-manager[1222]: <info>  (ttyACM1) opening serial port...
Jan 11 06:08:43 l05 dbus[1167]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: init!
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: update_system_hostname
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPluginIfupdown: management mode: unmanaged
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0)
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6/net/usb0, iface: usb0)
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6/net/usb0, iface: usb0): no ifupdown configuration found.
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlan0, iface: wlan0)
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: end _init.
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan 11 06:08:43 l05 NetworkManager[1260]:    Ifupdown: get unmanaged devices count: 0
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: (22169392) ... get_connections.
Jan 11 06:08:43 l05 NetworkManager[1260]:    SCPlugin-Ifupdown: (22169392) ... get_connections (managed=false): return empty list.
Jan 11 06:08:43 l05 NetworkManager[1260]:    keyfile: parsing Auto Ethernet ...
Jan 11 06:08:43 l05 NetworkManager[1260]:    keyfile:     read connection 'Auto Ethernet'
Jan 11 06:08:43 l05 NetworkManager[1260]:    keyfile: parsing wlan0101 ...
Jan 11 06:08:43 l05 NetworkManager[1260]:    keyfile:     read connection 'wlan0101'
Jan 11 06:08:43 l05 NetworkManager[1260]:    Ifupdown: get unmanaged devices count: 0
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> modem-manager is now available
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/ieee80211/phy0/rfkill1) (driver (unknown))
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/platform/hp-wmi/rfkill/rfkill2) (driver hp-wmi)
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> Networking is enabled by state file
Jan 11 06:08:43 l05 NetworkManager[1260]: <warn> failed to allocate link cache: (-10) Operation not supported
Jan 11 06:08:43 l05 modem-manager[1222]: <info>  (ttyACM2) opening serial port...
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (eth0): carrier is OFF
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (eth0): new Ethernet device (driver: 'e1000e' ifindex: 2)
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (eth0): now managed
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (eth0): bringing up device.
Jan 11 06:08:43 l05 kernel: [   11.006455] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Jan 11 06:08:43 l05 kernel: [   11.006519] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Jan 11 06:08:43 l05 kernel: [   11.006952] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Jan 11 06:08:43 l05 kernel: [   11.010325] HDMI: detected monitor SAMSUNG at connection type HDMI
Jan 11 06:08:43 l05 kernel: [   11.010327] HDMI: available speakers: FL/FR
Jan 11 06:08:43 l05 kernel: [   11.010330] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
Jan 11 06:08:43 l05 kernel: [   11.010332] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Jan 11 06:08:43 l05 kernel: [   11.010407] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Jan 11 06:08:43 l05 kernel: [   11.015741] HDMI: detected monitor SAMSUNG at connection type HDMI
Jan 11 06:08:43 l05 kernel: [   11.015744] HDMI: available speakers: FL/FR
Jan 11 06:08:43 l05 kernel: [   11.015747] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
Jan 11 06:08:43 l05 kernel: [   11.015824] HDMI status: Codec=3 Pin=6 Presence_Detect=0 ELD_Valid=0
Jan 11 06:08:43 l05 kernel: [   11.015905] HDMI status: Codec=3 Pin=7 Presence_Detect=0 ELD_Valid=0
Jan 11 06:08:43 l05 kernel: [   11.015966] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
Jan 11 06:08:43 l05 kernel: [   11.016038] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
Jan 11 06:08:43 l05 kernel: [   11.016100] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
Jan 11 06:08:43 l05 kernel: [   11.016161] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
Jan 11 06:08:43 l05 kernel: [   11.016217] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
Jan 11 06:08:43 l05 kernel: [   11.016275] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
Jan 11 06:08:43 l05 kernel: [   11.016332] input: HDA Intel PCH Dock Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
Jan 11 06:08:43 l05 kernel: [   11.017526] HDMI: detected monitor SAMSUNG at connection type HDMI
Jan 11 06:08:43 l05 kernel: [   11.017529] HDMI: available speakers: FL/FR
Jan 11 06:08:43 l05 kernel: [   11.017532] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
Jan 11 06:08:43 l05 kernel: [   11.034171] parport_pc 00:0a: reported by Plug and Play ACPI
Jan 11 06:08:43 l05 kernel: [   11.034236] parport0: PC-style at 0x378 (0x778), irq 5, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Jan 11 06:08:43 l05 kernel: [   11.057405] type=1400 audit(1389380923.702:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1375 comm="apparmor_parser"
Jan 11 06:08:43 l05 kernel: [   11.057687] type=1400 audit(1389380923.702:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1375 comm="apparmor_parser"
Jan 11 06:08:43 l05 kernel: [   11.058353] type=1400 audit(1389380923.706:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1379 comm="apparmor_parser"
Jan 11 06:08:43 l05 kernel: [   11.058716] type=1400 audit(1389380923.706:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1379 comm="apparmor_parser"
Jan 11 06:08:43 l05 kernel: [   11.060907] type=1400 audit(1389380923.706:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1376 comm="apparmor_parser"
Jan 11 06:08:43 l05 kernel: [   11.061401] type=1400 audit(1389380923.706:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1376 comm="apparmor_parser"
Jan 11 06:08:43 l05 kernel: [   11.061592] type=1400 audit(1389380923.706:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1376 comm="apparmor_parser"
Jan 11 06:08:43 l05 kernel: [   11.094897] hp_wmi: unknown device type 0x3
Jan 11 06:08:43 l05 kernel: [   11.110979] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input20
Jan 11 06:08:43 l05 cron[1421]: (CRON) INFO (pidfile fd = 3)
Jan 11 06:08:43 l05 anacron[1437]: Anacron 2.3 started on 2014-01-11
Jan 11 06:08:43 l05 acpid: starting up with proc fs
Jan 11 06:08:43 l05 acpid: 35 rules loaded
Jan 11 06:08:43 l05 acpid: waiting for events: event logging is off
Jan 11 06:08:43 l05 udev-configure-printer: add /devices/pnp0/00:0a/printer/lp0
Jan 11 06:08:43 l05 udev-configure-printer: Failed to get parent
Jan 11 06:08:43 l05 kernel: [   11.130141] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [   11.130268] lp0: using parport0 (interrupt-driven).
Jan 11 06:08:43 l05 cron[1460]: (CRON) STARTUP (fork ok)
Jan 11 06:08:43 l05 cron[1460]: (CRON) INFO (Running @reboot jobs)
Jan 11 06:08:43 l05 anacron[1437]: Will run job `cron.daily' in 5 min.
Jan 11 06:08:43 l05 anacron[1437]: Jobs will be executed sequentially
Jan 11 06:08:43 l05 dbus[1167]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (eth0): preparing device.
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (eth0): deactivating device (reason 'managed') [2]
Jan 11 06:08:43 l05 NetworkManager[1260]: <warn> failed to allocate link cache: (-10) Operation not supported
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (usb0): carrier is OFF
Jan 11 06:08:43 l05 NetworkManager[1260]: <error> [1389380923.838559] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (usb0): unable to read permanent MAC address (error 0)
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (usb0): new Ethernet device (driver: 'cdc_ncm' ifindex: 3)
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (usb0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (usb0): now managed
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (usb0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (usb0): bringing up device.
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (usb0): preparing device.
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (usb0): deactivating device (reason 'managed') [2]
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (wlan0): using nl80211 for WiFi device control
Jan 11 06:08:43 l05 NetworkManager[1260]: <warn> (wlan0): driver supports Access Point (AP) mode
Jan 11 06:08:43 l05 kernel: [   11.185926] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Jan 11 06:08:43 l05 kernel: [   11.186591] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 11 06:08:43 l05 kernel: [   11.186954] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 11 06:08:43 l05 kernel: [   11.189173] ADDRCONF(NETDEV_UP): usb0: link is not ready
Jan 11 06:08:43 l05 kernel: [   11.189530] ADDRCONF(NETDEV_UP): usb0: link is not ready
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 4)
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (wlan0): now managed
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan 11 06:08:43 l05 NetworkManager[1260]: <info> (wlan0): bringing up device.
Jan 11 06:08:43 l05 dbus[1167]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jan 11 06:08:43 l05 kernel: [   11.190822] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
Jan 11 06:08:43 l05 kernel: [   11.197226] cdc_ncm: usb0: network connection: disconnected
Jan 11 06:08:43 l05 kernel: [   11.197304] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
Jan 11 06:08:43 l05 kernel: [   11.213711] vboxdrv: Found 4 processor cores.
Jan 11 06:08:43 l05 bluetoothd[1235]: Listening for HCI events on hci0
Jan 11 06:08:43 l05 bluetoothd[1235]: HCI dev 0 up
Jan 11 06:08:43 l05 kernel: [   11.331062] vboxdrv: fAsync=0 offMin=0xe6 offMax=0xe48
Jan 11 06:08:43 l05 kernel: [   11.331122] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jan 11 06:08:43 l05 kernel: [   11.331125] vboxdrv: Successfully loaded version 4.3.4 (interface 0x001a0005).
Jan 11 06:08:43 l05 bluetoothd[1235]: Adapter /org/bluez/1235/hci0 has been enabled
Jan 11 06:08:44 l05 bluetoothd[1235]: Inquiry Cancel Failed with status 0x0c
Jan 11 06:08:44 l05 acpid: client connected from 1505[0:0]
Jan 11 06:08:44 l05 acpid: 1 client rule loaded
Jan 11 06:08:44 l05 kernel: [   11.495643] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
Jan 11 06:08:44 l05 kernel: [   11.502053] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
Jan 11 06:08:44 l05 kernel: [   11.539245] vboxpci: IOMMU not found (not registered)
Jan 11 06:08:44 l05 kernel: [   11.604797] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 11 06:08:44 l05 NetworkManager[1260]: <info> (wlan0): preparing device.
Jan 11 06:08:44 l05 NetworkManager[1260]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan 11 06:08:44 l05 dbus[1167]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jan 11 06:08:44 l05 NetworkManager[1260]: <info> found WWAN radio killswitch rfkill3 (at /sys/devices/platform/hp-wmi/rfkill/rfkill3) (driver hp-wmi)
Jan 11 06:08:44 l05 dbus[1167]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jan 11 06:08:44 l05 NetworkManager[1260]: <info> wpa_supplicant started
Jan 11 06:08:44 l05 kernel: [   11.637817] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 11 06:08:44 l05 NetworkManager[1260]: <info> (wlan0): supplicant interface state: starting -> ready
Jan 11 06:08:44 l05 NetworkManager[1260]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jan 11 06:08:44 l05 NetworkManager[1260]: <info> (wlan0): supplicant interface state: ready -> inactive
Jan 11 06:08:44 l05 NetworkManager[1260]: <warn> Trying to remove a non-existant call id.
Jan 11 06:08:44 l05 kernel: [   11.904524] Adding 8250364k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:8250364k SS
Jan 11 06:08:44 l05 kernel: [   11.978312] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1c0b1, caps: 0xf00133/0x640000/0xa2400
Jan 11 06:08:44 l05 kernel: [   12.021928] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input21
Jan 11 06:08:45 l05 kernel: [   12.368467] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1
Jan 11 06:08:45 l05 kernel: [   12.368514] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Jan 11 06:08:45 l05 modem-manager[1222]: <info>  (ttyACM0) closing serial port...
Jan 11 06:08:45 l05 modem-manager[1222]: <info>  (ttyACM0) serial port closed
Jan 11 06:08:45 l05 modem-manager[1222]: <info>  (ttyACM0) opening serial port...
Jan 11 06:08:45 l05 modem-manager[1222]: <info>  (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5 claimed port ttyACM0
Jan 11 06:08:45 l05 modem-manager[1222]: <info>  (ttyACM1) closing serial port...
Jan 11 06:08:45 l05 modem-manager[1222]: <info>  (ttyACM1) serial port closed
Jan 11 06:08:45 l05 modem-manager[1222]: <info>  (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5 claimed port ttyACM1
Jan 11 06:08:45 l05 modem-manager[1222]: <info>  (ttyACM2) closing serial port...
Jan 11 06:08:45 l05 modem-manager[1222]: <info>  (ttyACM2) serial port closed
Jan 11 06:08:45 l05 modem-manager[1222]: <info>  (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5 claimed port ttyACM2
Jan 11 06:08:45 l05 kernel: [   12.560329] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Jan 11 06:08:45 l05 kernel: [   12.560391] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Jan 11 06:08:45 l05 kernel: [   12.859802] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Jan 11 06:08:45 l05 kernel: [   12.863310] HDMI: detected monitor SAMSUNG at connection type HDMI
Jan 11 06:08:45 l05 kernel: [   12.863312] HDMI: available speakers: FL/FR
Jan 11 06:08:45 l05 kernel: [   12.863314] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
Jan 11 06:08:45 l05 kernel: [   12.896146] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 17000000, was 12000000
Jan 11 06:08:45 l05 dbus[1167]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jan 11 06:08:45 l05 dbus[1167]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jan 11 06:08:45 l05 accounts-daemon[1850]: started daemon version 0.6.15
Jan 11 06:08:45 l05 dbus[1167]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Jan 11 06:08:45 l05 dbus[1167]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Jan 11 06:08:46 l05 dbus[1167]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jan 11 06:08:46 l05 dbus[1167]: [system] Successfully activated service 'org.freedesktop.UPower'
Jan 11 06:08:46 l05 dbus[1167]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jan 11 06:08:46 l05 dbus[1167]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Successfully called chroot.
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Successfully dropped privileges.
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Successfully limited resources.
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Running.
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Canary thread running.
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Watchdog thread running.
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Successfully made thread 2130 of process 2130 (n/a) owned by '104' high priority at nice level -11.
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Supervising 1 threads of 1 processes of 1 users.
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Successfully made thread 2259 of process 2130 (n/a) owned by '104' RT at priority 5.
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Supervising 2 threads of 1 processes of 1 users.
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Successfully made thread 2260 of process 2130 (n/a) owned by '104' RT at priority 5.
Jan 11 06:08:46 l05 rtkit-daemon[2134]: Supervising 3 threads of 1 processes of 1 users.
Jan 11 06:08:46 l05 bluetoothd[1235]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/HFPAG
Jan 11 06:08:46 l05 bluetoothd[1235]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/A2DPSource
Jan 11 06:08:46 l05 bluetoothd[1235]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/A2DPSink
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> (eth0): carrier now ON (device state 20)
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Auto-activating connection 'Auto Ethernet'.
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) starting connection 'Auto Ethernet'
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 11 06:08:47 l05 kernel: [   14.858879] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Jan 11 06:08:47 l05 kernel: [   14.859320] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> dhclient started with pid 2263
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 11 06:08:47 l05 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jan 11 06:08:47 l05 dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jan 11 06:08:47 l05 dhclient: All rights reserved.
Jan 11 06:08:47 l05 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan 11 06:08:47 l05 dhclient:
Jan 11 06:08:47 l05 NetworkManager[1260]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan 11 06:08:47 l05 dhclient: Listening on LPF/eth0/10:1f:74:77:1b:e1
Jan 11 06:08:47 l05 dhclient: Sending on   LPF/eth0/10:1f:74:77:1b:e1
Jan 11 06:08:47 l05 dhclient: Sending on   Socket/fallback
Jan 11 06:08:47 l05 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan 11 06:08:47 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 255.255.255.255 port 67
Jan 11 06:08:47 l05 dhclient: DHCPOFFER of 192.168.0.4 from 192.168.0.1
Jan 11 06:08:49 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 11 06:08:49 l05 dhclient: bound to 19Jan 11 06:11:06 l05 kernel: imklog 5.8.6, log source = /proc/kmsg started.

```

```

Jan 11 06:45:10 l05 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1227" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jan 11 06:45:14 l05 anacron[1425]: Job `cron.daily' terminated
Jan 11 06:45:14 l05 anacron[1425]: Normal exit (1 job run)
Jan 11 06:58:17 l05 gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/hsiva is already mounted
Jan 11 07:06:21 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 11 07:06:22 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 11 07:06:22 l05 dhclient: bound to 192.168.0.4 -- renewal in 1618 seconds.
Jan 11 07:15:36 l05 gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/hsiva is already mounted
Jan 11 07:17:01 l05 CRON[5605]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 07:30:01 l05 CRON[5952]: (root) CMD (start -q anacron || :)
Jan 11 07:30:01 l05 anacron[5955]: Anacron 2.3 started on 2014-01-11
Jan 11 07:30:01 l05 anacron[5955]: Normal exit (0 jobs run)
Jan 11 07:33:20 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 11 07:33:21 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 11 07:33:21 l05 dhclient: bound to 192.168.0.4 -- renewal in 1700 seconds.
Jan 11 07:54:58 l05 kernel: [ 6234.551524] usb 4-1: USB disconnect, device number 2
Jan 11 07:54:58 l05 kernel: [ 6234.791230] usb 4-1: new SuperSpeed USB device number 3 using xhci_hcd
Jan 11 07:54:58 l05 kernel: [ 6234.807773] hub 4-1:1.0: USB hub found
Jan 11 07:54:58 l05 kernel: [ 6234.807792] hub 4-1:1.0: 4 ports detected
Jan 11 07:56:25 l05 gnome-screensaver-dialog: pam_ecryptfs: pam_sm_authenticate: /home/hsiva is already mounted
Jan 11 08:01:41 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 11 08:01:42 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 11 08:01:42 l05 dhclient: bound to 192.168.0.4 -- renewal in 1403 seconds.
Jan 11 08:17:01 l05 CRON[6887]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 11 08:25:05 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 11 08:25:06 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 11 08:25:06 l05 dhclient: bound to 192.168.0.4 -- renewal in 1479 seconds.
Jan 11 08:49:45 l05 dhclient: DHCPREQUEST of 192.168.0.4 on eth0 to 192.168.0.1 port 67
Jan 11 08:49:46 l05 dhclient: DHCPACK of 192.168.0.4 from 192.168.0.1
Jan 11 08:49:46 l05 dhclient: bound to 192.168.0.4 -- renewal in 1543 seconds.
Jan 11 08:54:27 l05 kernel: [ 9798.655281] usb 4-1: USB disconnect, device number 3
Jan 11 08:54:27 l05 kernel: [ 9798.895016] usb 4-1: new SuperSpeed USB device number 4 using xhci_hcd
Jan 11 08:54:27 l05 kernel: [ 9798.911811] hub 4-1:1.0: USB hub found
Jan 11 08:54:27 l05 kernel: [ 9798.911853] hub 4-1:1.0: 4 ports detected
Jan 11 09:11:11 l05 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jan 11 09:11:11 l05 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1233" x-info="http://www.rsyslog.com"] start
Jan 11 09:11:11 l05 rsyslogd: rsyslogd's groupid changed to 103
Jan 11 09:11:11 l05 rsyslogd: rsyslogd's userid changed to 101
Jan 11 09:11:11 l05 rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jan 11 09:11:11 l05 modem-manager[1225]: <info>  Loaded plugin Wavecom
Jan 11 09:11:11 l05 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 11 09:11:11 l05 kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 11 09:11:11 l05 kernel: [    0.000000] Linux version 3.2.0-58-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 (Ubuntu 3.2.0-58.88-generic 3.2.53)
Jan 11 09:11:11 l05 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-58-generic root=UUID=2e4355ef-517f-478a-be6b-63ce5ab552ea ro quiet splash vt.handoff=7
Jan 11 09:11:11 l05 kernel: [    0.000000] KERNEL supported cpus:
Jan 11 09:11:11 l05 kernel: [    0.000000]   Intel GenuineIntel
Jan 11 09:11:11 l05 kernel: [    0.000000]   AMD AuthenticAMD
Jan 11 09:11:11 l05 kernel: [    0.000000]   Centaur CentaurHauls
Jan 11 09:11:11 l05 kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040004000 (usable)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 0000000040004000 - 0000000040005000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 0000000040005000 - 00000000b8b9d000 (usable)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000b8b9d000 - 00000000b9d40000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9d40000 - 00000000b9fb3000 (usable)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fb3000 - 00000000b9fc0000 (ACPI NVS)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fc0000 - 00000000b9fff000 (ACPI data)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fff000 - 00000000ba000000 (usable)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000ba000000 - 00000000bf200000 (reserved)
Jan 11 09:11:11 l05 modem-manager[1225]: <info>  Loaded plugin ZTE
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jan 11 09:11:11 l05 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000023ee00000 (usable)
Jan 11 09:11:11 l05 kernel: [    0.000000] NX (Execute Disable) protection: active
Jan 11 09:11:11 l05 kernel: [    0.000000] SMBIOS 2.7 present.
Jan 11 09:11:11 l05 kernel: [    0.000000] DMI: Hewlett-Packard HP EliteBook 2170p/1815, BIOS 68IMT Ver. F.43 10/07/2013
```

---

### Post by snooze101 on 2014-01-12
```
Jan  3 12:43:57 l05 kernel: [  262.607613] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = 20:e5:2a:f1:e5:a0 tid = 6
Jan  3 12:46:56 l05 AptDaemon: INFO: Quitting due to inactivity
Jan  3 12:46:56 l05 AptDaemon: INFO: Quitting was requested
Jan  3 12:55:43 l05 kernel: [  968.444538] hp_wmi: Unknown event_id - 8 - 0x1
Jan  3 12:55:55 l05 kernel: [  979.685497] e1000e 0000:00:19.0: PME# enabled
Jan  3 12:56:16 l05 kernel: [ 1001.190255] usb 4-1: new SuperSpeed USB device number 2 using xhci_hcd
Jan  3 12:56:16 l05 kernel: [ 1001.207088] hub 4-1:1.0: USB hub found
Jan  3 12:56:16 l05 kernel: [ 1001.207134] hub 4-1:1.0: 4 ports detected
Jan  3 12:56:17 l05 kernel: [ 1001.445881] usb 3-1: new high-speed USB device number 3 using xhci_hcd
Jan  3 12:56:17 l05 kernel: [ 1001.462587] hub 3-1:1.0: USB hub found
Jan  3 12:56:17 l05 kernel: [ 1001.462649] hub 3-1:1.0: 4 ports detected
Jan  3 12:56:17 l05 kernel: [ 1001.733543] usb 3-1.4: new low-speed USB device number 4 using xhci_hcd
Jan  3 12:56:17 l05 kernel: [ 1001.753280] usb 3-1.4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Jan  3 12:56:17 l05 kernel: [ 1001.753301] usb 3-1.4: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
Jan  3 12:56:17 l05 kernel: [ 1001.756413] input: HID 1017:0002 as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.4/3-1.4:1.0/input/input20
Jan  3 12:56:17 l05 kernel: [ 1001.756695] generic-usb 0003:1017:0002.0004: input,hidraw3: USB HID v1.00 Keyboard [HID 1017:0002] on usb-0000:00:14.0-1.4/input0
Jan  3 12:56:17 l05 mtp-probe: checking bus 3, device 4: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.4"
Jan  3 12:56:17 l05 mtp-probe: bus: 3, device: 4 was not an MTP device
Jan  3 12:56:17 l05 kernel: [ 1001.761279] input: HID 1017:0002 as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.4/3-1.4:1.1/input/input21
Jan  3 12:56:17 l05 kernel: [ 1001.761903] generic-usb 0003:1017:0002.0005: input,hidraw4: USB HID v1.00 Mouse [HID 1017:0002] on usb-0000:00:14.0-1.4/input1
Jan  3 12:56:18 l05 kernel: [ 1002.668894] e1000e 0000:00:19.0: BAR 0: set to [mem 0xd0700000-0xd071ffff] (PCI address [0xd0700000-0xd071ffff])
Jan  3 12:56:18 l05 kernel: [ 1002.668913] e1000e 0000:00:19.0: BAR 1: set to [mem 0xd073a000-0xd073afff] (PCI address [0xd073a000-0xd073afff])
Jan  3 12:56:18 l05 kernel: [ 1002.668930] e1000e 0000:00:19.0: BAR 2: set to [io  0x2060-0x207f] (PCI address [0x2060-0x207f])
Jan  3 12:56:18 l05 kernel: [ 1002.668965] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Jan  3 12:56:18 l05 kernel: [ 1002.669008] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Jan  3 12:56:18 l05 kernel: [ 1002.669068] e1000e 0000:00:19.0: PME# disabled
Jan  3 12:56:18 l05 kernel: [ 1002.669222] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Jan  3 12:56:18 l05 anacron[4739]: Anacron 2.3 started on 2014-01-03
Jan  3 12:56:18 l05 anacron[4739]: Normal exit (0 jobs run)
Jan  3 12:56:21 l05 kernel: [ 1005.881875] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Jan  3 12:56:21 l05 kernel: [ 1005.883754] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> (eth0): carrier now ON (device state 20)
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Auto-activating connection 'Auto Ethernet'.
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) starting connection 'Auto Ethernet'
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> dhclient started with pid 4866
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan  3 12:56:21 l05 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Jan  3 12:56:21 l05 dhclient: Copyright 2004-2011 Internet Systems Consortium.
Jan  3 12:56:21 l05 dhclient: All rights reserved.
Jan  3 12:56:21 l05 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan  3 12:56:21 l05 dhclient:
Jan  3 12:56:21 l05 NetworkManager[1233]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jan  3 12:56:21 l05 dhclient: Listening on LPF/eth0/10:1f:74:77:1b:e1
Jan  3 12:56:21 l05 dhclient: Sending on   LPF/eth0/10:1f:74:77:1b:e1
Jan  3 12:56:21 l05 dhclient: Sending on   Socket/fallback
Jan  3 12:56:21 l05 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan  3 12:56:21 l05 dhclient: DHCPREQUEST of 192.168.0.2 on eth0 to 255.255.255.255 port 67
Jan  3 12:56:21 l05 dhclient: DHCPOFFER of 192.168.0.2 from 192.168.0.1
Jan  3 12:56:22 l05 dhclient: DHCPACK of 192.168.0.2 from 192.168.0.1
Jan  3 12:56:22 l05 dhclient: bound to 192.168.0.2 -- renewal in 1753 seconds.
Jan  3 12:56:22 l05 NetworkManager[1233]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jan  3 12:56:22 l05 NetworkManager[1233]: <info>   address 192.168.0.2
Jan  3 12:56:22 l05 NetworkManager[1233]: <info>   prefix 24 (255.255.255.0)
Jan  3 12:56:22 l05 NetworkManager[1233]: <info>   gateway 192.168.0.1
Jan  3 12:56:22 l05 NetworkManager[1233]: <info>   nameserver '61.9.194.49'
Jan  3 12:56:22 l05 NetworkManager[1233]: <info>   nameserver '61.9.195.193'
Jan  3 12:56:22 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jan  3 12:56:22 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jan  3 12:56:22 l05 avahi-daemon[1290]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.2.
Jan  3 12:56:22 l05 avahi-daemon[1290]: New relevant interface eth0.IPv4 for mDNS.
Jan  3 12:56:22 l05 avahi-daemon[1290]: Registering new address record for 192.168.0.2 on eth0.IPv4.
Jan  3 12:56:23 l05 avahi-daemon[1290]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::121f:74ff:fe77:1be1.
Jan  3 12:56:23 l05 avahi-daemon[1290]: New relevant interface eth0.IPv6 for mDNS.
Jan  3 12:56:23 l05 avahi-daemon[1290]: Registering new address record for fe80::121f:74ff:fe77:1be1 on eth0.*.
Jan  3 12:56:23 l05 NetworkManager[1233]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jan  3 12:56:23 l05 dnsmasq[2863]: setting upstream servers from DBus
Jan  3 12:56:23 l05 dnsmasq[2863]: using nameserver 61.9.195.193#53
Jan  3 12:56:23 l05 dnsmasq[2863]: using nameserver 61.9.194.49#53
Jan  3 12:56:23 l05 dnsmasq[2863]: using nameserver 61.9.194.49#53
Jan  3 12:56:23 l05 dnsmasq[2863]: using nameserver 61.9.195.193#53
Jan  3 12:56:23 l05 NetworkManager[1233]: <info> Policy set 'wlan0101' (wlan0) as default for IPv4 routing and DNS.
Jan  3 12:56:23 l05 NetworkManager[1233]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan  3 12:56:23 l05 NetworkManager[1233]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jan  3 12:56:23 l05 dnsmasq[2863]: setting upstream servers from DBus
Jan  3 12:56:23 l05 dnsmasq[2863]: using nameserver 61.9.194.49#53
Jan  3 12:56:23 l05 dnsmasq[2863]: using nameserver 61.9.195.193#53
Jan  3 12:56:23 l05 dnsmasq[2863]: using nameserver 61.9.194.49#53
Jan  3 12:56:23 l05 dnsmasq[2863]: using nameserver 61.9.195.193#53
Jan  3 12:56:23 l05 NetworkManager[1233]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS.
Jan  3 12:56:23 l05 NetworkManager[1233]: <info> Activation (eth0) successful, device activated.
Jan  3 12:56:23 l05 NetworkManager[1233]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jan  3 12:56:23 l05 dbus[1156]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan  3 12:56:23 l05 dbus[1156]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  3 12:56:23 l05 kernel: [ 1008.029974] CIFS VFS: cifs_mount failed w/return code = -6
Jan  3 12:56:23 l05 kernel: [ 1008.031549] CIFS VFS: cifs_mount failed w/return code = -6
Jan  3 12:56:32 l05 kernel: [ 1016.554263] eth0: no IPv6 routers present
Jan  3 12:56:32 l05 ntpdate[4908]: adjust time server 91.189.94.4 offset 0.083699 sec
Jan  3 13:09:14 l05 dhclient: DHCPREQUEST of 192.168.0.58 on wlan0 to 192.168.0.1 port 67
Jan  3 13:09:17 l05 dhclient: DHCPREQUEST of 192.168.0.58 on wlan0 to 192.168.0.1 port 67
Jan  3 13:09:17 l05 dhclient: DHCPNAK from 192.168.0.1
Jan  3 13:09:17 l05 NetworkManager[1233]: <info> (wlan0): DHCPv4 state changed reboot -> expire
Jan  3 13:09:17 l05 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  3 13:09:17 l05 NetworkManager[1233]: <info> (wlan0): DHCPv4 state changed expire -> preinit
Jan  3 13:09:17 l05 dhclient: DHCPREQUEST of 192.168.0.59 on wlan0 to 255.255.255.255 port 67
Jan  3 13:09:17 l05 dhclient: DHCPOFFER of 192.168.0.59 from 192.168.0.1
Jan  3 13:09:18 l05 dhclient: DHCPACK of 192.168.0.59 from 192.168.0.1
Jan  3 13:09:18 l05 dhclient: bound to 192.168.0.59 -- renewal in 1545 seconds.
Jan  3 13:09:18 l05 NetworkManager[1233]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jan  3 13:09:18 l05 NetworkManager[1233]: <info>   address 192.168.0.59
Jan  3 13:09:18 l05 NetworkManager[1233]: <info>   prefix 24 (255.255.255.0)
Jan  3 13:09:18 l05 NetworkManager[1233]: <info>   gateway 192.168.0.1
Jan  3 13:09:18 l05 NetworkManager[1233]: <info>   nameserver '61.9.194.49'
Jan  3 13:09:18 l05 NetworkManager[1233]: <info>   nameserver '61.9.195.193'
Jan  3 13:09:18 l05 NetworkManager[1233]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jan  3 13:09:18 l05 dnsmasq[2863]: setting upstream servers from DBus
Jan  3 13:09:18 l05 dnsmasq[2863]: using nameserver 61.9.194.49#53
Jan  3 13:09:18 l05 dnsmasq[2863]: using nameserver 61.9.195.193#53
Jan  3 13:09:18 l05 avahi-daemon[1290]: Withdrawing address record for 192.168.0.58 on wlan0.
Jan  3 13:09:18 l05 avahi-daemon[1290]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.58.
Jan  3 13:09:18 l05 avahi-daemon[1290]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  3 13:09:18 l05 avahi-daemon[1290]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.59.
Jan  3 13:09:18 l05 avahi-daemon[1290]: New relevant interface wlan0.IPv4 for mDNS.
Jan  3 13:09:18 l05 avahi-daemon[1290]: Registering new address record for 192.168.0.59 on wlan0.IPv4.
Jan  3 13:09:19 l05 NetworkManager[1233]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jan  3 13:09:19 l05 dnsmasq[2863]: setting upstream servers from DBus
Jan  3 13:09:19 l05 dnsmasq[2863]: using nameserver 61.9.195.193#53
Jan  3 13:09:19 l05 dnsmasq[2863]: using nameserver 61.9.194.49#53
Jan  3 13:09:19 l05 dnsmasq[2863]: using nameserver 61.9.194.49#53
Jan  3 13:09:19 l05 dnsmasq[2863]: using nameserver 61.9.195.193#53
Jan  3 13:09:19 l05 NetworkManager[1233]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS.
Jan  3 13:09:19 l05 dbus[1156]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan  3 13:09:19 l05 dbus[1156]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  3 13:14:05 l05 kernel: [ 2068.292997] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:05 l05 kernel: [ 2068.293007] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:05 l05 kernel: [ 2068.293020] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:05 l05 kernel: [ 2068.293793] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:05 l05 kernel: [ 2068.293803] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:05 l05 kernel: [ 2068.293814] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:05 l05 kernel: [ 2068.293825] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:05 l05 kernel: [ 2068.293886] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:05 l05 kernel: [ 2068.293892] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:05 l05 kernel: [ 2068.293919] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:05 l05 kernel: [ 2068.293933] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:06 l05 kernel: [ 2069.316111] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:06 l05 kernel: [ 2069.316121] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:06 l05 kernel: [ 2069.316133] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:06 l05 kernel: [ 2069.316453] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:06 l05 kernel: [ 2069.316546] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:06 l05 kernel: [ 2069.316557] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:06 l05 kernel: [ 2069.316567] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:14:06 l05 kernel: [ 2069.316628] CIFS VFS: Server 192.168.0.10 has not responded in 300 seconds. Reconnecting...
Jan  3 13:17:01 l05 CRON[5328]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  3 13:25:35 l05 dhclient: DHCPREQUEST of 192.168.0.2 on eth0 to 192.168.0.1 port 67
Jan  3 13:25:36 l05 dhclient: DHCPACK of 192.168.0.2 from 192.168.0.1
Jan  3 13:25:36 l05 dhclient: bound to 192.168.0.2 -- renewal in 1652 seconds.
Jan  3 13:25:36 l05 NetworkManager[1233]: <info> (eth0): DHCPv4 state changed bound -> renew
Jan  3 13:25:36 l05 NetworkManager[1233]: <info>   address 192.168.0.2
Jan  3 13:25:36 l05 NetworkManager[1233]: <info>   prefix 24 (255.255.255.0)
Jan  3 13:25:36 l05 NetworkManager[1233]: <info>   gateway 192.168.0.1
Jan  3 13:25:36 l05 NetworkManager[1233]: <info>   nameserver '61.9.194.49'
Jan  3 13:25:36 l05 NetworkManager[1233]: <info>   nameserver '61.9.195.193'
Jan  3 13:25:36 l05 dbus[1156]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan  3 13:25:36 l05 dbus[1156]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  3 13:35:03 l05 dhclient: DHCPREQUEST of 192.168.0.59 on wlan0 to 192.168.0.1 port 67
Jan  3 13:35:06 l05 dhclient: DHCPREQUEST of 192.168.0.59 on wlan0 to 192.168.0.1 port 67
Jan  3 13:35:06 l05 dhclient: DHCPNAK from 192.168.0.1
Jan  3 13:35:06 l05 NetworkManager[1233]: <info> (wlan0): DHCPv4 state changed bound -> expire
Jan  3 13:35:06 l05 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  3 13:35:06 l05 NetworkManager[1233]: <info> (wlan0): DHCPv4 state changed expire -> preinit
Jan  3 13:35:06 l05 dhclient: DHCPREQUEST of 192.168.0.60 on wlan0 to 255.255.255.255 port 67
Jan  3 13:35:06 l05 dhclient: DHCPOFFER of 192.168.0.60 from 192.168.0.1
Jan  3 13:35:07 l05 dhclient: DHCPACK of 192.168.0.60 from 192.168.0.1
Jan  3 13:35:07 l05 dhclient: bound to 192.168.0.60 -- renewal in 1641 seconds.
Jan  3 13:35:07 l05 NetworkManager[1233]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jan  3 13:35:07 l05 NetworkManager[1233]: <info>   address 192.168.0.60
Jan  3 13:35:07 l05 NetworkManager[1233]: <info>   prefix 24 (255.255.255.0)
Jan  3 13:35:07 l05 NetworkManager[1233]: <info>   gateway 192.168.0.1
Jan  3 13:35:07 l05 NetworkManager[1233]: <info>   nameserver '61.9.194.49'
Jan  3 13:35:07 l05 NetworkManager[1233]: <info>   nameserver '61.9.195.193'
Jan  3 13:35:07 l05 NetworkManager[1233]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jan  3 13:35:07 l05 dnsmasq[2863]: setting upstream servers from DBus
Jan  3 13:35:07 l05 dnsmasq[2863]: using nameserver 61.9.194.49#53
Jan  3 13:35:07 l05 dnsmasq[2863]: using nameserver 61.9.195.193#53
Jan  3 13:35:07 l05 avahi-daemon[1290]: Withdrawing address record for 192.168.0.59 on wlan0.
Jan  3 13:35:07 l05 avahi-daemon[1290]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.59.
Jan  3 13:35:07 l05 avahi-daemon[1290]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  3 13:35:07 l05 avahi-daemon[1290]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.60.
Jan  3 13:35:07 l05 avahi-daemon[1290]: New relevant interface wlan0.IPv4 for mDNS.
Jan  3 13:35:07 l05 avahi-daemon[1290]: Registering new address record for 192.168.0.60 on wlan0.IPv4.
Jan  3 13:35:08 l05 NetworkManager[1233]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jan  3 13:35:08 l05 dnsmasq[2863]: setting upstream servers from DBus
Jan  3 13:35:08 l05 dnsmasq[2863]: using nameserver 61.9.195.193#53
Jan  3 13:35:08 l05 dnsmasq[2863]: using nameserver 61.9.194.49#53
Jan  3 13:35:08 l05 dnsmasq[2863]: using nameserver 61.9.194.49#53
Jan  3 13:35:08 l05 dnsmasq[2863]: using nameserver 61.9.195.193#53
Jan  3 13:35:08 l05 NetworkManager[1233]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS.
Jan  3 13:35:08 l05 dbus[1156]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan  3 13:35:08 l05 dbus[1156]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'

Jan  3 14:27:52 l05 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jan  3 14:27:52 l05 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1210" x-info="http://www.rsyslog.com"] start
Jan  3 14:27:52 l05 rsyslogd: rsyslogd's groupid changed to 103
Jan  3 14:27:52 l05 rsyslogd: rsyslogd's userid changed to 101
Jan  3 14:27:52 l05 rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jan  3 14:27:52 l05 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  3 14:27:52 l05 kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  3 14:27:52 l05 kernel: [    0.000000] Linux version 3.2.0-57-generic (buildd@toyol) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 (Ubuntu 3.2.0-57.87-generic 3.2.52)
Jan  3 14:27:52 l05 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-57-generic root=UUID=2e4355ef-517f-478a-be6b-63ce5ab552ea ro quiet splash vt.handoff=7
Jan  3 14:27:52 l05 kernel: [    0.000000] KERNEL supported cpus:
Jan  3 14:27:52 l05 kernel: [    0.000000]   Intel GenuineIntel
Jan  3 14:27:52 l05 kernel: [    0.000000]   AMD AuthenticAMD
Jan  3 14:27:52 l05 kernel: [    0.000000]   Centaur CentaurHauls
Jan  3 14:27:52 l05 kernel: [    0.000000] BIOS-provided physical RAM map:
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040004000 (usable)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000040004000 - 0000000040005000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000040005000 - 00000000b8b9d000 (usable)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000b8b9d000 - 00000000b9d40000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9d40000 - 00000000b9fb3000 (usable)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fb3000 - 00000000b9fc0000 (ACPI NVS)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fc0000 - 00000000b9fff000 (ACPI data)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fff000 - 00000000ba000000 (usable)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000ba000000 - 00000000bf200000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jan  3 14:27:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000023ee00000 (usable)
Jan  3 14:27:52 l05 kernel: [    0.000000] NX (Execute Disable) protection: active
Jan  3 14:27:52 l05 kernel: [    0.000000] SMBIOS 2.7 present.
Jan  3 14:27:52 l05 kernel: [    0.000000] DMI: Hewlett-Packard HP EliteBook 2170p/1815, BIOS 68IMT Ver. F.43 10/07/2013
```

Auto Sleep activated, then Resume activated, then laptop lock up requiring reset

```
Jan  1 07:10:09 l05 dbus[1135]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  1 07:17:01 l05 CRON[6675]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  1 07:21:26 l05 kernel: [ 2300.128853] hp_wmi: Unknown event_id - 8 - 0x1
Jan  1 07:26:56 l05 NetworkManager[1226]: <info> sleep requested (sleeping: no  enabled: yes)
Jan  1 07:26:56 l05 NetworkManager[1226]: <info> sleeping or disabling...
Jan  1 07:26:56 l05 NetworkManager[1226]: <info> (eth0): now unmanaged
Jan  1 07:26:56 l05 NetworkManager[1226]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jan  1 07:26:56 l05 NetworkManager[1226]: <info> (eth0): cleaning up...
Jan  1 07:26:56 l05 NetworkManager[1226]: <info> (eth0): taking down device.
Jan  1 07:26:56 l05 kernel: [ 2630.086258] device eth0 left promiscuous mode
Jan  1 07:26:56 l05 kernel: [ 2630.100490] e1000e 0000:00:19.0: BAR 0: set to [mem 0xd0700000-0xd071ffff] (PCI address [0xd0700000-0xd071ffff])
Jan  1 07:26:56 l05 kernel: [ 2630.100507] e1000e 0000:00:19.0: BAR 1: set to [mem 0xd073a000-0xd073afff] (PCI address [0xd073a000-0xd073afff])
Jan  1 07:26:56 l05 kernel: [ 2630.100521] e1000e 0000:00:19.0: BAR 2: set to [io  0x2060-0x207f] (PCI address [0x2060-0x207f])
Jan  1 07:26:56 l05 kernel: [ 2630.100564] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Jan  1 07:26:56 l05 kernel: [ 2630.100610] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Jan  1 07:26:56 l05 kernel: [ 2630.100679] e1000e 0000:00:19.0: PME# disabled
Jan  1 07:26:56 l05 kernel: [ 2630.100829] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Jan  1 07:26:57 l05 kernel: [ 2630.357891] e1000e 0000:00:19.0: PME# enabled
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (usb0): now unmanaged
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (usb0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (usb0): cleaning up...
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (usb0): taking down device.
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (wlan0): now unmanaged
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (wlan0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (wlan0): deactivating device (reason 'sleeping') [37]
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 3243
Jan  1 07:26:57 l05 avahi-daemon[1262]: Withdrawing address record for fe80::c685:8ff:fe03:30ea on wlan0.
Jan  1 07:26:57 l05 avahi-daemon[1262]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::c685:8ff:fe03:30ea.
Jan  1 07:26:57 l05 avahi-daemon[1262]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jan  1 07:26:57 l05 avahi-daemon[1262]: Withdrawing address record for 192.168.0.44 on wlan0.
Jan  1 07:26:57 l05 avahi-daemon[1262]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.44.
Jan  1 07:26:57 l05 kernel: [ 2630.659523] wlan0: deauthenticating from 20:e5:2a:f1:e5:a0 by local choice (reason=3)
Jan  1 07:26:57 l05 NetworkManager[1226]: <warn> DNS: plugin dnsmasq update failed
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (wlan0): removing resolv.conf from /sbin/resolvconf
Jan  1 07:26:57 l05 avahi-daemon[1262]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  1 07:26:57 l05 dnsmasq[3247]: setting upstream servers from DBus
Jan  1 07:26:57 l05 kernel: [ 2630.668219] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan  1 07:26:57 l05 kernel: [ 2630.668232] cfg80211: Restoring regulatory settings
Jan  1 07:26:57 l05 kernel: [ 2630.668242] cfg80211: Calling CRDA to update world regulatory domain
Jan  1 07:26:57 l05 wpa_supplicant[1684]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Jan  1 07:26:57 l05 kernel: [ 2630.680464] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jan  1 07:26:57 l05 kernel: [ 2630.680468] cfg80211: World regulatory domain updated:
Jan  1 07:26:57 l05 kernel: [ 2630.680469] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  1 07:26:57 l05 kernel: [ 2630.680472] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  1 07:26:57 l05 kernel: [ 2630.680474] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  1 07:26:57 l05 kernel: [ 2630.680477] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  1 07:26:57 l05 kernel: [ 2630.680479] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  1 07:26:57 l05 kernel: [ 2630.680481] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (wlan0): cleaning up...
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (wlan0): taking down device.
Jan  1 07:26:57 l05 dbus[1135]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (ttyACM0): now unmanaged
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (ttyACM0): device state change: disconnected -> unmanaged (reason 'sleeping') [30 10 37]
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (ttyACM0): cleaning up...
Jan  1 07:26:57 l05 NetworkManager[1226]: <info> (ttyACM0): taking down device.
Jan  1 07:26:57 l05 dbus[1135]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jan  1 07:26:58 l05 anacron[7447]: Anacron 2.3 started on 2014-01-01
Jan  1 07:26:58 l05 anacron[7447]: Will run job `cron.daily' in 5 min.
Jan  1 07:26:58 l05 anacron[7447]: Will run job `cron.weekly' in 10 min.
Jan  1 07:26:58 l05 anacron[7447]: Jobs will be executed sequentially
Jan  1 07:26:58 l05 kernel: [ 2631.290940] e1000e 0000:00:19.0: BAR 0: set to [mem 0xd0700000-0xd071ffff] (PCI address [0xd0700000-0xd071ffff])
Jan  1 07:26:58 l05 kernel: [ 2631.290948] e1000e 0000:00:19.0: BAR 1: set to [mem 0xd073a000-0xd073afff] (PCI address [0xd073a000-0xd073afff])
Jan  1 07:26:58 l05 kernel: [ 2631.290955] e1000e 0000:00:19.0: BAR 2: set to [io  0x2060-0x207f] (PCI address [0x2060-0x207f])
Jan  1 07:26:58 l05 kernel: [ 2631.290971] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Jan  1 07:26:58 l05 kernel: [ 2631.290989] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Jan  1 07:26:58 l05 kernel: [ 2631.291034] e1000e 0000:00:19.0: PME# disabled
Jan  1 07:26:59 l05 kernel: [ 2632.274277] init: anacron main process (7447) killed by TERM signal
Jan  1 07:26:59 l05 kernel: [ 2632.360378] PM: Syncing filesystems ... done.
Jan  1 07:26:59 l05 kernel: [ 2632.363642] PM: Preparing system for mem sleep
Jan  1 07:27:00 l05 kernel: [ 2633.136785] mmc0: card e624 removed
Jan  1 07:41:50 l05 bluetoothd[1212]: HCI dev 0 down
Jan  1 07:41:50 l05 rtkit-daemon[2180]: The canary thread is apparently starving. Taking action.
Jan  1 07:41:50 l05 rtkit-daemon[2180]: Demoting known real-time threads.
Jan  1 07:41:50 l05 rtkit-daemon[2180]: Successfully demoted thread 2723 of process 2602 (n/a).
Jan  1 07:41:50 l05 bluetoothd[1212]: Adapter /org/bluez/1212/hci0 has been disabled
Jan  1 07:41:50 l05 bluetoothd[1212]: HCI dev 0 unregistered
Jan  1 07:41:50 l05 bluetoothd[1212]: Stopping hci0 event socket
Jan  1 07:41:50 l05 bluetoothd[1212]: Unregister path: /org/bluez/1212/hci0
Jan  1 07:41:50 l05 rtkit-daemon[2180]: Successfully demoted thread 2722 of process 2602 (n/a).
Jan  1 07:41:50 l05 kernel: [ 2633.150175] Freezing user space processes ... (elapsed 0.01 seconds) done.
Jan  1 07:41:50 l05 kernel: [ 2633.164608] Freezing remaining freezable tasks ... (elapsed 3.55 seconds) done.
Jan  1 07:41:50 l05 kernel: [ 2636.712022] PM: Entering mem sleep
Jan  1 07:41:50 l05 kernel: [ 2636.712044] Suspending console(s) (use no_console_suspend to debug)
Jan  1 07:41:50 l05 kernel: [ 2636.712764] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Jan  1 07:41:50 l05 kernel: [ 2636.713872] sd 0:0:0:0: [sda] Stopping disk
Jan  1 07:41:50 l05 kernel: [ 2636.769696] parport_pc 00:09: disabled
Jan  1 07:41:50 l05 kernel: [ 2636.875785] PM: suspend of drv:tpm_tis dev:00:04 complete after 106.208 msecs
Jan  1 07:41:50 l05 kernel: [ 2636.875883] ehci_hcd 0000:00:1d.0: PCI INT A disabled
Jan  1 07:41:50 l05 kernel: [ 2636.875948] ehci_hcd 0000:00:1a.0: PCI INT A disabled
Jan  1 07:41:50 l05 kernel: [ 2636.876650] ACPI handle has no context!
Jan  1 07:41:50 l05 kernel: [ 2636.876963] sdhci-pci 0000:02:00.0: PCI INT A disabled
Jan  1 07:41:50 l05 kernel: [ 2636.972122] e1000e 0000:00:19.0: PME# enabled
Jan  1 07:41:50 l05 kernel: [ 2636.972134] e1000e 0000:00:19.0: wake-up capability enabled by ACPI
Jan  1 07:41:50 l05 kernel: [ 2636.980142] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
Jan  1 07:41:50 l05 kernel: [ 2636.987610] PM: suspend of drv:e1000e dev:0000:00:19.0 complete after 111.796 msecs
Jan  1 07:41:50 l05 kernel: [ 2637.000694] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D3
Jan  1 07:41:50 l05 kernel: [ 2637.000703] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 124.948 msecs
Jan  1 07:41:50 l05 kernel: [ 2637.402450] PM: suspend of drv:sd dev:0:0:0:0 complete after 690.581 msecs
Jan  1 07:41:50 l05 kernel: [ 2637.402470] PM: suspend of drv:scsi dev:target0:0:0 complete after 690.567 msecs
Jan  1 07:41:50 l05 kernel: [ 2637.402481] PM: suspend of drv:scsi dev:host0 complete after 634.046 msecs
Jan  1 07:41:50 l05 kernel: [ 2637.431040] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 555.898 msecs
Jan  1 07:41:50 l05 kernel: [ 2637.431058] PM: suspend of drv: dev:pci0000:00 complete after 553.426 msecs
Jan  1 07:41:50 l05 kernel: [ 2637.431087] PM: suspend of devices complete after 719.834 msecs
Jan  1 07:41:50 l05 kernel: [ 2637.431090] PM: suspend devices took 0.720 seconds
Jan  1 07:41:50 l05 kernel: [ 2637.447209] ehci_hcd 0000:00:1d.0: PME# enabled
Jan  1 07:41:50 l05 kernel: [ 2637.447222] ehci_hcd 0000:00:1d.0: wake-up capability enabled by ACPI
Jan  1 07:41:50 l05 kernel: [ 2637.463060] ehci_hcd 0000:00:1a.0: PME# enabled
Jan  1 07:41:50 l05 kernel: [ 2637.463078] ehci_hcd 0000:00:1a.0: wake-up capability enabled by ACPI
Jan  1 07:41:50 l05 kernel: [ 2637.494992] xhci_hcd 0000:00:14.0: PME# enabled
Jan  1 07:41:50 l05 kernel: [ 2637.495005] xhci_hcd 0000:00:14.0: wake-up capability enabled by ACPI
Jan  1 07:41:50 l05 kernel: [ 2637.510977] PM: late suspend of devices complete after 79.984 msecs
Jan  1 07:41:50 l05 kernel: [ 2637.511331] ACPI: Preparing to enter system sleep state S3
Jan  1 07:41:50 l05 kernel: [ 2637.567107] PM: Saving platform NVS memory
Jan  1 07:41:50 l05 kernel: [ 2637.567237] Disabling non-boot CPUs ...
Jan  1 07:41:50 l05 kernel: [ 2637.670716] CPU 1 is now offline
Jan  1 07:41:50 l05 kernel: [ 2637.774581] CPU 2 is now offline
Jan  1 07:41:50 l05 kernel: [ 2637.775638] Broke affinity for irq 1
Jan  1 07:41:50 l05 kernel: [ 2637.878457] CPU 3 is now offline
Jan  1 07:41:50 l05 kernel: [ 2637.878898] Extended CMOS year: 2000
Jan  1 07:41:50 l05 kernel: [ 2637.879335] ACPI: Low-level resume complete
Jan  1 07:41:50 l05 kernel: [ 2637.879376] PM: Restoring platform NVS memory
Jan  1 07:41:50 l05 kernel: [ 2637.879666] Extended CMOS year: 2000
Jan  1 07:41:50 l05 kernel: [ 2637.879707] Enabling non-boot CPUs ...
Jan  1 07:41:50 l05 kernel: [ 2637.879821] Booting Node 0 Processor 1 APIC 0x1
Jan  1 07:41:50 l05 kernel: [ 2637.879823] smpboot cpu 1: start_ip = 98000
Jan  1 07:41:50 l05 kernel: [ 2637.890838] Calibrating delay loop (skipped) already calibrated this CPU
Jan  1 07:41:50 l05 kernel: [ 2637.911758] NMI watchdog enabled, takes one hw-pmu counter.
Jan  1 07:41:50 l05 kernel: [ 2637.912090] CPU1 is up
Jan  1 07:41:50 l05 kernel: [ 2637.912182] Booting Node 0 Processor 2 APIC 0x2
Jan  1 07:41:50 l05 kernel: [ 2637.912184] smpboot cpu 2: start_ip = 98000
Jan  1 07:41:50 l05 kernel: [ 2637.923198] Calibrating delay loop (skipped) already calibrated this CPU
Jan  1 07:41:50 l05 kernel: [ 2637.944153] NMI watchdog enabled, takes one hw-pmu counter.
Jan  1 07:41:50 l05 kernel: [ 2637.944488] CPU2 is up
Jan  1 07:41:50 l05 kernel: [ 2637.944566] Booting Node 0 Processor 3 APIC 0x3
Jan  1 07:41:50 l05 kernel: [ 2637.944568] smpboot cpu 3: start_ip = 98000
Jan  1 07:41:50 l05 kernel: [ 2637.955581] Calibrating delay loop (skipped) already calibrated this CPU
Jan  1 07:41:50 l05 kernel: [ 2637.976585] NMI watchdog enabled, takes one hw-pmu counter.
Jan  1 07:41:50 l05 kernel: [ 2637.976906] CPU3 is up
Jan  1 07:41:50 l05 kernel: [ 2637.981483] ACPI: Waking up from system sleep state S3
Jan  1 07:41:50 l05 kernel: [ 2638.251348] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Jan  1 07:41:50 l05 kernel: [ 2638.251359] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
Jan  1 07:41:50 l05 kernel: [ 2638.251382] xhci_hcd 0000:00:14.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Jan  1 07:41:50 l05 kernel: [ 2638.251399] xhci_hcd 0000:00:14.0: restoring config space at offset 0x4 (was 0x4, writing 0xd0720004)
Jan  1 07:41:50 l05 kernel: [ 2638.251406] xhci_hcd 0000:00:14.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900402)
Jan  1 07:41:50 l05 kernel: [ 2638.251435] xhci_hcd 0000:00:14.0: wake-up capability disabled by ACPI
Jan  1 07:41:50 l05 kernel: [ 2638.251440] xhci_hcd 0000:00:14.0: PME# disabled
Jan  1 07:41:50 l05 kernel: [ 2638.251452] mei 0000:00:16.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Jan  1 07:41:50 l05 kernel: [ 2638.251467] mei 0000:00:16.0: restoring config space at offset 0x4 (was 0xfedb0004, writing 0xd0734004)
Jan  1 07:41:50 l05 kernel: [ 2638.251491] serial 0000:00:16.3: restoring config space at offset 0xf (was 0x200, writing 0x205)
Jan  1 07:41:50 l05 kernel: [ 2638.251505] serial 0000:00:16.3: restoring config space at offset 0x5 (was 0x0, writing 0xd073b000)
Jan  1 07:41:50 l05 kernel: [ 2638.251510] serial 0000:00:16.3: restoring config space at offset 0x4 (was 0x1, writing 0x2091)
Jan  1 07:41:50 l05 kernel: [ 2638.251517] serial 0000:00:16.3: restoring config space at offset 0x1 (was 0xb00000, writing 0xb00007)
Jan  1 07:41:50 l05 kernel: [ 2638.251540] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Jan  1 07:41:50 l05 kernel: [ 2638.251553] e1000e 0000:00:19.0: restoring config space at offset 0x6 (was 0x1, writing 0x2061)
Jan  1 07:41:50 l05 kernel: [ 2638.251562] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100007)
Jan  1 07:41:50 l05 kernel: [ 2638.251588] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Jan  1 07:41:50 l05 kernel: [ 2638.251605] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0739000)
Jan  1 07:41:50 l05 kernel: [ 2638.251613] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
Jan  1 07:41:50 l05 kernel: [ 2638.251630] ehci_hcd 0000:00:1a.0: wake-up capability disabled by ACPI
Jan  1 07:41:50 l05 kernel: [ 2638.251635] ehci_hcd 0000:00:1a.0: PME# disabled
Jan  1 07:41:50 l05 kernel: [ 2638.251665] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100002)
Jan  1 07:41:50 l05 kernel: [ 2638.251694] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Jan  1 07:41:50 l05 kernel: [ 2638.251704] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Jan  1 07:41:50 l05 kernel: [ 2638.251709] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xd060d060)
Jan  1 07:41:50 l05 kernel: [ 2638.251714] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
Jan  1 07:41:50 l05 kernel: [ 2638.251719] pcieport 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0x10100)
Jan  1 07:41:50 l05 kernel: [ 2638.251727] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jan  1 07:41:50 l05 kernel: [ 2638.251733] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jan  1 07:41:50 l05 kernel: [ 2638.251778] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x30a)
Jan  1 07:41:50 l05 kernel: [ 2638.251788] pcieport 0000:00:1c.2: restoring config space at offset 0x9 (was 0x1fff1, writing 0xbf21bf21)
Jan  1 07:41:50 l05 kernel: [ 2638.251799] pcieport 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jan  1 07:41:50 l05 kernel: [ 2638.251805] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
Jan  1 07:41:50 l05 kernel: [ 2638.251850] pcieport 0000:00:1c.3: restoring config space at offset 0xf (was 0x400, writing 0x40a)
Jan  1 07:41:50 l05 kernel: [ 2638.251860] pcieport 0000:00:1c.3: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
Jan  1 07:41:50 l05 kernel: [ 2638.251866] pcieport 0000:00:1c.3: restoring config space at offset 0x8 (was 0x0, writing 0xd040d040)
Jan  1 07:41:50 l05 kernel: [ 2638.251871] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0x0, writing 0x200000f0)
Jan  1 07:41:50 l05 kernel: [ 2638.251876] pcieport 0000:00:1c.3: restoring config space at offset 0x6 (was 0x0, writing 0x30300)
Jan  1 07:41:50 l05 kernel: [ 2638.251883] pcieport 0000:00:1c.3: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
Jan  1 07:41:50 l05 kernel: [ 2638.251889] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
Jan  1 07:41:50 l05 kernel: [ 2638.251930] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Jan  1 07:41:50 l05 kernel: [ 2638.251947] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0738000)
Jan  1 07:41:50 l05 kernel: [ 2638.251955] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
Jan  1 07:41:50 l05 kernel: [ 2638.251972] ehci_hcd 0000:00:1d.0: wake-up capability disabled by ACPI
Jan  1 07:41:50 l05 kernel: [ 2638.251976] ehci_hcd 0000:00:1d.0: PME# disabled
Jan  1 07:41:50 l05 kernel: [ 2638.252039] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00403, writing 0x2b00407)
Jan  1 07:41:50 l05 kernel: [ 2638.252091] sdhci-pci 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
Jan  1 07:41:50 l05 kernel: [ 2638.252102] sdhci-pci 0000:02:00.0: restoring config space at offset 0xc (was 0x0, writing 0xffff0000)
Jan  1 07:41:50 l05 kernel: [ 2638.252128] sdhci-pci 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xd0503000)
Jan  1 07:41:50 l05 kernel: [ 2638.252135] sdhci-pci 0000:02:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
Jan  1 07:41:50 l05 kernel: [ 2638.252144] sdhci-pci 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Jan  1 07:41:50 l05 kernel: [ 2638.252200] pci 0000:02:00.2: restoring config space at offset 0xf (was 0x1ff, writing 0x10a)
Jan  1 07:41:50 l05 kernel: [ 2638.252233] pci 0000:02:00.2: restoring config space at offset 0x4 (was 0x0, writing 0xd0502000)
Jan  1 07:41:50 l05 kernel: [ 2638.252240] pci 0000:02:00.2: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
Jan  1 07:41:50 l05 kernel: [ 2638.252249] pci 0000:02:00.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100003)
Jan  1 07:41:50 l05 kernel: [ 2638.252387] iwlwifi 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
Jan  1 07:41:50 l05 kernel: [ 2638.252429] iwlwifi 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd0400004)
Jan  1 07:41:50 l05 kernel: [ 2638.252438] iwlwifi 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jan  1 07:41:50 l05 kernel: [ 2638.252450] iwlwifi 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
Jan  1 07:41:50 l05 kernel: [ 2638.252646] PM: early resume of devices complete after 1.352 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.252715] i915 0000:00:02.0: setting latency timer to 64
Jan  1 07:41:50 l05 kernel: [ 2638.252737] xhci_hcd 0000:00:14.0: setting latency timer to 64
Jan  1 07:41:50 l05 kernel: [ 2638.252849] mei 0000:00:16.0: irq 45 for MSI/MSI-X
Jan  1 07:41:50 l05 kernel: [ 2638.252907] e1000e 0000:00:19.0: wake-up capability disabled by ACPI
Jan  1 07:41:50 l05 kernel: [ 2638.252912] e1000e 0000:00:19.0: PME# disabled
Jan  1 07:41:50 l05 kernel: [ 2638.252927] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  1 07:41:50 l05 kernel: [ 2638.252940] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jan  1 07:41:50 l05 kernel: [ 2638.253010] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  1 07:41:50 l05 kernel: [ 2638.253021] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jan  1 07:41:50 l05 kernel: [ 2638.253025] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
Jan  1 07:41:50 l05 kernel: [ 2638.253051] ahci 0000:00:1f.2: setting latency timer to 64
Jan  1 07:41:50 l05 kernel: [ 2638.261379] sdhci-pci 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan  1 07:41:50 l05 kernel: [ 2638.261395] sdhci-pci 0000:02:00.0: setting latency timer to 64
Jan  1 07:41:50 l05 kernel: [ 2638.266743] sd 0:0:0:0: [sda] Starting disk
Jan  1 07:41:50 l05 kernel: [ 2638.273663] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
Jan  1 07:41:50 l05 kernel: [ 2638.273669] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
Jan  1 07:41:50 l05 kernel: [ 2638.273676] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
Jan  1 07:41:50 l05 kernel: [ 2638.273681] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
Jan  1 07:41:50 l05 kernel: [ 2638.273689] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jan  1 07:41:50 l05 kernel: [ 2638.273697] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
Jan  1 07:41:50 l05 kernel: [ 2638.273741] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
Jan  1 07:41:50 l05 kernel: [ 2638.355977] PM: resume of drv:e1000e dev:0000:00:19.0 complete after 103.208 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.438576] PM: resume of drv:hub dev:2-1:1.0 complete after 176.739 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.438597] PM: resume of drv: dev:ep_81 complete after 176.743 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.438605] PM: resume of drv: dev:ep_00 complete after 176.732 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.438625] PM: resume of drv: dev:ep_00 complete after 176.827 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.438628] PM: resume of drv:hub dev:1-1:1.0 complete after 176.863 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.438650] PM: resume of drv: dev:ep_81 complete after 176.867 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486893] PM: resume of drv:usb dev:1-1.1:1.0 complete after 224.905 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486900] PM: resume of drv: dev:ep_00 complete after 224.832 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486913] PM: resume of drv: dev:ep_01 complete after 224.913 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486920] PM: resume of drv: dev:ep_81 complete after 224.903 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486925] PM: resume of drv:cdc_ncm dev:1-1.5:1.6 complete after 224.314 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486929] PM: resume of drv: dev:ep_82 complete after 224.893 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486933] PM: resume of drv:cdc_ncm dev:1-1.5:1.7 complete after 224.281 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486937] PM: resume of drv:cdc_wdm dev:1-1.5:1.5 complete after 224.356 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486940] PM: resume of drv: dev:ep_83 complete after 224.885 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486946] PM: resume of drv:cdc_acm dev:1-1.5:1.4 complete after 224.418 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486950] PM: resume of drv:cdc_wdm dev:1-1.5:1.8 complete after 224.281 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486956] PM: resume of drv: dev:ep_88 complete after 224.358 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486959] PM: resume of drv:cdc_acm dev:1-1.5:1.3 complete after 224.466 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486967] PM: resume of drv: dev:ep_85 complete after 224.141 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486971] PM: resume of drv:cdc_acm dev:1-1.5:1.9 complete after 224.269 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486975] PM: resume of drv: dev:ep_05 complete after 224.165 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486980] PM: resume of drv:cdc_acm dev:1-1.5:1.2 complete after 224.537 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486984] PM: resume of drv: dev:ep_82 complete after 224.420 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486988] PM: resume of drv:cdc_acm dev:1-1.5:1.10 complete after 224.240 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486991] PM: resume of drv: dev:ep_86 complete after 224.356 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.486996] PM: resume of drv:cdc_acm dev:1-1.5:1.1 complete after 224.583 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.487000] PM: resume of drv: dev:ep_02 complete after 224.448 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.487005] PM: resume of drv: dev:ep_87 complete after 224.316 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.487008] PM: resume of drv: dev:ep_00 complete after 224.206 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.487012] PM: resume of drv: dev:ep_01 complete after 224.547 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.487016] PM: resume of drv:usb dev:1-1.5:1.0 complete after 224.624 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.487021] PM: resume of drv: dev:ep_89 complete after 224.502 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.487026] PM: resume of drv: dev:ep_81 complete after 224.545 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.487030] PM: resume of drv: dev:ep_83 complete after 224.251 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.487033] PM: resume of drv: dev:ep_84 complete after 224.308 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.487038] PM: resume of drv: dev:ep_8a complete after 224.608 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.487044] PM: resume of drv: dev:ep_03 complete after 224.278 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.498067] watchdog: only one watchdog can use /dev/watchdog.
Jan  1 07:41:50 l05 kernel: [ 2638.498071] watchdog: error registering /dev/watchdog (err=-16).
Jan  1 07:41:50 l05 kernel: [ 2638.498072] mei: unable to register watchdog device.
Jan  1 07:41:50 l05 kernel: [ 2638.510620] usb 1-1.3: reset high-speed USB device number 5 using ehci_hcd
Jan  1 07:41:50 l05 kernel: [ 2638.586322] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jan  1 07:41:50 l05 kernel: [ 2638.594314] ata4: SATA link down (SStatus 0 SControl 300)
Jan  1 07:41:50 l05 kernel: [ 2638.602300] ata6: SATA link down (SStatus 0 SControl 300)
Jan  1 07:41:50 l05 kernel: [ 2638.674455] usb 1-1.2: reset full-speed USB device number 4 using ehci_hcd
Jan  1 07:41:50 l05 kernel: [ 2638.690734] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Jan  1 07:41:50 l05 kernel: [ 2638.690740] ata1.00: supports DRM functions and may not be fully accessible
Jan  1 07:41:50 l05 kernel: [ 2638.769196] btusb 1-1.2:1.0: no reset_resume for driver btusb?
Jan  1 07:41:50 l05 kernel: [ 2638.769200] btusb 1-1.2:1.1: no reset_resume for driver btusb?
Jan  1 07:41:50 l05 kernel: [ 2638.887200] PM: resume of drv:uvcvideo dev:1-1.3:1.1 complete after 625.408 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.887206] PM: resume of drv: dev:ep_00 complete after 625.393 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.887220] PM: resume of drv:uvcvideo dev:1-1.3:1.0 complete after 625.466 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.887237] PM: resume of drv: dev:ep_87 complete after 625.466 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.912685] PM: resume of drv:i915 dev:0000:00:02.0 complete after 660.830 msecs
Jan  1 07:41:50 l05 kernel: [ 2638.967332] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Jan  1 07:41:50 l05 kernel: [ 2638.967339] ata1.00: supports DRM functions and may not be fully accessible
Jan  1 07:41:50 l05 kernel: [ 2639.000959] ata1.00: configured for UDMA/100
Jan  1 07:41:50 l05 kernel: [ 2639.017929] PM: resume of drv:usb dev:1-1.2:1.1 complete after 756.442 msecs
Jan  1 07:41:50 l05 kernel: [ 2639.017934] PM: resume of drv:usb dev:1-1.2:1.0 complete after 756.513 msecs
Jan  1 07:41:50 l05 kernel: [ 2639.017950] PM: resume of drv: dev:ep_81 complete after 756.518 msecs
Jan  1 07:41:50 l05 kernel: [ 2639.017954] PM: resume of drv: dev:ep_00 complete after 756.407 msecs
Jan  1 07:41:50 l05 kernel: [ 2639.017959] PM: resume of drv: dev:ep_03 complete after 756.454 msecs
Jan  1 07:41:50 l05 kernel: [ 2639.017974] PM: resume of drv: dev:ep_02 complete after 756.527 msecs
Jan  1 07:41:50 l05 kernel: [ 2639.017977] PM: resume of drv: dev:ep_83 complete after 756.456 msecs
Jan  1 07:41:50 l05 kernel: [ 2639.017981] PM: resume of drv: dev:ep_82 complete after 756.516 msecs
Jan  1 07:41:50 l05 kernel: [ 2639.195070] PM: resume of drv:sd dev:0:0:0:0 complete after 934.339 msecs
Jan  1 07:41:50 l05 kernel: [ 2639.195135] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 934.391 msecs
Jan  1 07:41:50 l05 kernel: [ 2640.391923] tpm_tis 00:04: tpm_transmit: tpm_send: error -62
Jan  1 07:41:50 l05 kernel: [ 2640.391928] PM: resume of drv:tpm_tis dev:00:04 complete after 2003.630 msecs
Jan  1 07:41:50 l05 kernel: [ 2640.392997] parport_pc 00:09: activated
Jan  1 07:41:50 l05 kernel: [ 2640.432392] PM: resume of devices complete after 2182.535 msecs
Jan  1 07:41:50 l05 kernel: [ 2640.432795] PM: resume devices took 2.184 seconds
Jan  1 07:41:50 l05 kernel: [ 2640.432934] PM: Finishing wakeup.
Jan  1 07:41:50 l05 rtkit-daemon[2180]: Successfully demoted thread 2602 of process 2602 (n/a).
Jan  1 07:41:50 l05 rtkit-daemon[2180]: Demoted 3 threads.
Jan  1 07:41:50 l05 acpid: client 1451[0:0] has disconnected
Jan  1 07:41:50 l05 bluetoothd[1212]: Endpoint unregistered: sender=:1.48 path=/MediaEndpoint/A2DPSink
Jan  1 07:41:50 l05 bluetoothd[1212]: Endpoint unregistered: sender=:1.48 path=/MediaEndpoint/A2DPSource
Jan  1 07:41:50 l05 bluetoothd[1212]: Endpoint unregistered: sender=:1.48 path=/MediaEndpoint/HFPAG
Jan  1 07:41:50 l05 CRON[7916]: (root) CMD (start -q anacron || :)
Jan  1 07:41:50 l05 kernel: [ 2640.432935] Restarting tasks ... done.
Jan  1 07:41:50 l05 anacron[7919]: Anacron 2.3 started on 2014-01-01
Jan  1 07:41:50 l05 anacron[7919]: Will run job `cron.daily' in 5 min.
Jan  1 07:41:50 l05 anacron[7919]: Will run job `cron.weekly' in 10 min.
Jan  1 07:41:50 l05 anacron[7919]: Jobs will be executed sequentially
Jan  1 07:41:50 l05 bluetoothd[1212]: HCI dev 0 registered
Jan  1 07:41:50 l05 bluetoothd[1212]: Listening for HCI events on hci0
Jan  1 07:41:50 l05 kernel: [ 2640.472974] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 17000000, was 12060000
Jan  1 07:41:50 l05 kernel: [ 2640.496759] video LNXVIDEO:01: Restoring backlight state
Jan  1 07:41:50 l05 kernel: [ 2640.551024] usb 2-1.8: new full-speed USB device number 3 using ehci_hcd
Jan  1 07:41:50 l05 kernel: [ 2640.568005] hub 2-1:1.0: unable to enumerate USB device on port 8
Jan  1 07:41:50 l05 acpid: client connected from 1451[0:0]
Jan  1 07:41:50 l05 acpid: 1 client rule loaded
Jan  1 07:41:50 l05 bluetoothd[1212]: HCI dev 0 up
Jan  1 07:41:50 l05 bluetoothd[1212]: Adapter /org/bluez/1212/hci0 has been enabled
Jan  1 07:41:50 l05 bluetoothd[1212]: Endpoint registered: sender=:1.48 path=/MediaEndpoint/HFPAG
Jan  1 07:41:50 l05 bluetoothd[1212]: Endpoint registered: sender=:1.48 path=/MediaEndpoint/A2DPSource
Jan  1 07:41:50 l05 bluetoothd[1212]: Endpoint registered: sender=:1.48 path=/MediaEndpoint/A2DPSink
Jan  1 07:41:50 l05 kernel: [ 2640.868368] mmc0: new SDHC card at address e624
Jan  1 07:41:50 l05 kernel: [ 2640.870538] mmcblk0: mmc0:e624 SU32G 29.7 GiB
Jan  1 07:41:51 l05 kernel: [ 2640.883465]  mmcblk0: p1
Jan  1 07:41:51 l05 kernel: [ 2641.215247] init: anacron main process (7919) killed by TERM signal
Jan  1 07:42:14 l05 kernel: [ 2664.696445] BUG: soft lockup - CPU#0 stuck for 22s! [kworker/0:1:5349]
Jan  1 07:42:14 l05 kernel: [ 2664.696448] Modules linked in: des_generic md4 nls_utf8 cifs dm_crypt pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) tpm_infineon snd_hda_codec_hdmi snd_hda_codec_idt bnep rfcomm nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc arc4 ppdev hp_wmi sparse_keymap uvcvideo btusb bluetooth videodev v4l2_compat_ioctl32 cdc_ncm usbnet cdc_wdm cdc_acm joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd iwlwifi mac80211 psmouse serio_raw cfg80211 soundcore snd_page_alloc mei(C) parport_pc tpm_tis hp_accel lis3lv02d input_polldev mac_hid lp parport mmc_block wmi sdhci_pci sdhci i915 e1000e drm_kms_helper drm usbhid hid i2c_algo_bit video
Jan  1 07:42:14 l05 kernel: [ 2664.696501] CPU 0
Jan  1 07:42:14 l05 kernel: [ 2664.696502] Modules linked in: des_generic md4 nls_utf8 cifs dm_crypt pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) tpm_infineon snd_hda_codec_hdmi snd_hda_codec_idt bnep rfcomm nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc arc4 ppdev hp_wmi sparse_keymap uvcvideo btusb bluetooth videodev v4l2_compat_ioctl32 cdc_ncm usbnet cdc_wdm cdc_acm joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd iwlwifi mac80211 psmouse serio_raw cfg80211 soundcore snd_page_alloc mei(C) parport_pc tpm_tis hp_accel lis3lv02d input_polldev mac_hid lp parport mmc_block wmi sdhci_pci sdhci i915 e1000e drm_kms_helper drm usbhid hid i2c_algo_bit video
Jan  1 07:42:14 l05 kernel: [ 2664.696541]
Jan  1 07:42:14 l05 kernel: [ 2664.696544] Pid: 5349, comm: kworker/0:1 Tainted: G         C O 3.2.0-57-generic #87-Ubuntu Hewlett-Packard HP EliteBook 2170p/1815
Jan  1 07:42:14 l05 kernel: [ 2664.696548] RIP: 0010:[<ffffffff8131c50c>]  [<ffffffff8131c50c>] __read_lock_failed+0xc/0x20
Jan  1 07:42:14 l05 kernel: [ 2664.696555] RSP: 0018:ffff88022c059d30  EFLAGS: 00000297
Jan  1 07:42:14 l05 kernel: [ 2664.696557] RAX: 0000000000000002 RBX: ffff88022c059cd0 RCX: ffffffffffffffff
Jan  1 07:42:14 l05 kernel: [ 2664.696559] RDX: ffff88022c059d88 RSI: 0000000000000000 RDI: ffff88022d4bfc58
Jan  1 07:42:14 l05 kernel: [ 2664.696561] RBP: ffff88022c059d30 R08: 0000000000000001 R09: 0000000000000001
Jan  1 07:42:14 l05 kernel: [ 2664.696563] R10: 0000000000000001 R11: 0000000000000000 R12: ffff88022c059cb0
Jan  1 07:42:14 l05 kernel: [ 2664.696565] R13: 0000002000000000 R14: 0000000000000000 R15: 0000000000000000
Jan  1 07:42:14 l05 kernel: [ 2664.696567] FS:  0000000000000000(0000) GS:ffff88023ea00000(0000) knlGS:0000000000000000
Jan  1 07:42:14 l05 kernel: [ 2664.696569] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Jan  1 07:42:14 l05 kernel: [ 2664.696571] CR2: 00007fb9b4fe2f80 CR3: 0000000001c05000 CR4: 00000000001426f0
Jan  1 07:42:14 l05 kernel: [ 2664.696573] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Jan  1 07:42:14 l05 kernel: [ 2664.696575] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Jan  1 07:42:14 l05 kernel: [ 2664.696578] Process kworker/0:1 (pid: 5349, threadinfo ffff88022c058000, task ffff88004207c500)
Jan  1 07:42:14 l05 kernel: [ 2664.696580] Stack:
Jan  1 07:42:14 l05 kernel: [ 2664.696581]  ffff88022c059d40 ffffffff816615d3 ffff88022c059d70 ffffffff81519c58
Jan  1 07:42:14 l05 kernel: [ 2664.696585]  ffff8802312b5840 ffff8802312b5840 ffff88023ea17300 ffff88023ea0e480
Jan  1 07:42:14 l05 kernel: [ 2664.696588]  ffff88022c059db0 ffffffff814e224d ffffffff814e18e0 ffff880200000002
Jan  1 07:42:14 l05 kernel: [ 2664.696592] Call Trace:
Jan  1 07:42:14 l05 kernel: [ 2664.696597]  [<ffffffff816615d3>] _raw_read_lock+0x13/0x20
Jan  1 07:42:14 l05 kernel: [ 2664.696602]  [<ffffffff81519c58>] led_trigger_event+0x28/0x80
Jan  1 07:42:14 l05 kernel: [ 2664.696606]  [<ffffffff814e224d>] power_supply_update_bat_leds+0x4d/0x110
Jan  1 07:42:14 l05 kernel: [ 2664.696610]  [<ffffffff814e18e0>] ? __power_supply_is_system_supplied+0x50/0x50
Jan  1 07:42:14 l05 kernel: [ 2664.696614]  [<ffffffff814e235d>] power_supply_update_leds+0x4d/0x70
Jan  1 07:42:14 l05 kernel: [ 2664.696617]  [<ffffffff814e186c>] power_supply_changed_work+0x3c/0x60
Jan  1 07:42:14 l05 kernel: [ 2664.696622]  [<ffffffff81085cf7>] process_one_work+0x127/0x470
Jan  1 07:42:14 l05 kernel: [ 2664.696626]  [<ffffffff81086b68>] ? maybe_create_worker+0xf8/0x100
Jan  1 07:42:14 l05 kernel: [ 2664.696630]  [<ffffffff81086e04>] worker_thread+0x164/0x370
Jan  1 07:42:14 l05 kernel: [ 2664.696634]  [<ffffffff81086ca0>] ? manage_workers.isra.31+0x130/0x130
Jan  1 07:42:14 l05 kernel: [ 2664.696637]  [<ffffffff8108b64c>] kthread+0x8c/0xa0
Jan  1 07:42:14 l05 kernel: [ 2664.696642]  [<ffffffff8166bcf4>] kernel_thread_helper+0x4/0x10
Jan  1 07:42:14 l05 kernel: [ 2664.696645]  [<ffffffff8108b5c0>] ? flush_kthread_worker+0xa0/0xa0
Jan  1 07:42:14 l05 kernel: [ 2664.696649]  [<ffffffff8166bcf0>] ? gs_change+0x13/0x13
Jan  1 07:42:14 l05 kernel: [ 2664.696650] Code: 48 89 e5 f0 81 07 00 00 10 00 f3 90 81 3f 00 00 10 00 75 f6 f0 81 2f 00 00 10 00 75 e6 5d c3 55 48 89 e5 f0 ff 07 f3 90 83 3f 01 <78> f9 f0 ff 0f 78 f1 5d c3 90 90 90 90 90 90 90 90 90 90 90 57
Jan  1 07:42:14 l05 kernel: [ 2664.696682] Call Trace:
Jan  1 07:42:14 l05 kernel: [ 2664.696684]  [<ffffffff816615d3>] _raw_read_lock+0x13/0x20
Jan  1 07:42:14 l05 kernel: [ 2664.696688]  [<ffffffff81519c58>] led_trigger_event+0x28/0x80
Jan  1 07:42:14 l05 kernel: [ 2664.696692]  [<ffffffff814e224d>] power_supply_update_bat_leds+0x4d/0x110
Jan  1 07:42:14 l05 kernel: [ 2664.696695]  [<ffffffff814e18e0>] ? __power_supply_is_system_supplied+0x50/0x50
Jan  1 07:42:14 l05 kernel: [ 2664.696699]  [<ffffffff814e235d>] power_supply_update_leds+0x4d/0x70
Jan  1 07:42:14 l05 kernel: [ 2664.696702]  [<ffffffff814e186c>] power_supply_changed_work+0x3c/0x60
Jan  1 07:42:14 l05 kernel: [ 2664.696705]  [<ffffffff81085cf7>] process_one_work+0x127/0x470
Jan  1 07:42:14 l05 kernel: [ 2664.696708]  [<ffffffff81086b68>] ? maybe_create_worker+0xf8/0x100
Jan  1 07:42:14 l05 kernel: [ 2664.696712]  [<ffffffff81086e04>] worker_thread+0x164/0x370
Jan  1 07:42:14 l05 kernel: [ 2664.696715]  [<ffffffff81086ca0>] ? manage_workers.isra.31+0x130/0x130
Jan  1 07:42:14 l05 kernel: [ 2664.696718]  [<ffffffff8108b64c>] kthread+0x8c/0xa0
Jan  1 07:42:14 l05 kernel: [ 2664.696722]  [<ffffffff8166bcf4>] kernel_thread_helper+0x4/0x10
Jan  1 07:42:14 l05 kernel: [ 2664.696725]  [<ffffffff8108b5c0>] ? flush_kthread_worker+0xa0/0xa0
Jan  1 07:42:14 l05 kernel: [ 2664.696729]  [<ffffffff8166bcf0>] ? gs_change+0x13/0x13

Jan  1 07:43:07 l05 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jan  1 07:43:07 l05 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1234" x-info="http://www.rsyslog.com"] start
Jan  1 07:43:07 l05 rsyslogd: rsyslogd's groupid changed to 103
Jan  1 07:43:07 l05 rsyslogd: rsyslogd's userid changed to 101
Jan  1 07:43:07 l05 rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jan  1 07:43:07 l05 sm-notify[1079]: Version 1.2.5 starting
Jan  1 07:43:07 l05 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  1 07:43:07 l05 kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  1 07:43:07 l05 kernel: [    0.000000] Linux version 3.2.0-57-generic (buildd@toyol) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 (Ubuntu 3.2.0-57.87-generic 3.2.52)
Jan  1 07:43:07 l05 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-57-generic root=UUID=2e4355ef-517f-478a-be6b-63ce5ab552ea ro quiet splash vt.handoff=7
Jan  1 07:43:07 l05 kernel: [    0.000000] KERNEL supported cpus:
Jan  1 07:43:07 l05 kernel: [    0.000000]   Intel GenuineIntel
```

```
Dec 26 09:04:52 l05 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec 26 09:04:52 l05 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1267" x-info="http://www.rsyslog.com"] start
Dec 26 09:04:52 l05 rsyslogd: rsyslogd's groupid changed to 103
Dec 26 09:04:52 l05 rsyslogd: rsyslogd's userid changed to 101
Dec 26 09:04:52 l05 rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> NetworkManager (version 0.9.4.0) is starting...
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> DNS: loaded plugin dnsmasq
Dec 26 09:04:52 l05 sm-notify[1109]: Version 1.2.5 starting
Dec 26 09:04:52 l05 kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 26 09:04:52 l05 kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 26 09:04:52 l05 kernel: [    0.000000] Linux version 3.2.0-57-generic (buildd@toyol) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 (Ubuntu 3.2.0-57.87-generic 3.2.52)
Dec 26 09:04:52 l05 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-57-generic root=UUID=2e4355ef-517f-478a-be6b-63ce5ab552ea ro quiet splash vt.handoff=7
Dec 26 09:04:52 l05 kernel: [    0.000000] KERNEL supported cpus:
Dec 26 09:04:52 l05 kernel: [    0.000000]   Intel GenuineIntel
Dec 26 09:04:52 l05 kernel: [    0.000000]   AMD AuthenticAMD
Dec 26 09:04:52 l05 kernel: [    0.000000]   Centaur CentaurHauls
Dec 26 09:04:52 l05 kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040004000 (usable)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000040004000 - 0000000040005000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000040005000 - 00000000b8b9d000 (usable)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000b8b9d000 - 00000000b9d40000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9d40000 - 00000000b9fb3000 (usable)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fb3000 - 00000000b9fc0000 (ACPI NVS)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fc0000 - 00000000b9fff000 (ACPI data)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000b9fff000 - 00000000ba000000 (usable)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000ba000000 - 00000000bf200000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000023ee00000 (usable)
Dec 26 09:04:52 l05 kernel: [    0.000000] NX (Execute Disable) protection: active
Dec 26 09:04:52 l05 kernel: [    0.000000] SMBIOS 2.7 present.
Dec 26 09:04:52 l05 kernel: [    0.000000] DMI: Hewlett-Packard HP EliteBook 2170p/1815, BIOS 68IMT Ver. F.43 10/07/2013
Dec 26 09:04:52 l05 kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec 26 09:04:52 l05 kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Dec 26 09:04:52 l05 kernel: [    0.000000] No AGP bridge found
Dec 26 09:04:52 l05 kernel: [    0.000000] last_pfn = 0x23ee00 max_arch_pfn = 0x400000000
Dec 26 09:04:52 l05 kernel: [    0.000000] MTRR default type: uncachable
Dec 26 09:04:52 l05 kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 26 09:04:52 l05 kernel: [    0.000000]   00000-9FFFF write-back
Dec 26 09:04:52 l05 kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 26 09:04:52 l05 kernel: [    0.000000]   C0000-FFFFF write-protect
Dec 26 09:04:52 l05 kernel: [    0.000000] MTRR variable ranges enabled:
Dec 26 09:04:52 l05 kernel: [    0.000000]   0 base 0FF800000 mask FFF800000 write-protect
Dec 26 09:04:52 l05 kernel: [    0.000000]   1 base 000000000 mask F80000000 write-back
Dec 26 09:04:52 l05 kernel: [    0.000000]   2 base 080000000 mask FC0000000 write-back
Dec 26 09:04:52 l05 kernel: [    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
Dec 26 09:04:52 l05 kernel: [    0.000000]   4 base 0BB000000 mask FFF000000 uncachable
Dec 26 09:04:52 l05 kernel: [    0.000000]   5 base 100000000 mask F00000000 write-back
Dec 26 09:04:52 l05 kernel: [    0.000000]   6 base 200000000 mask FC0000000 write-back
Dec 26 09:04:52 l05 kernel: [    0.000000]   7 base 23F000000 mask FFF000000 uncachable
Dec 26 09:04:52 l05 kernel: [    0.000000]   8 base 23EE00000 mask FFFE00000 uncachable
Dec 26 09:04:52 l05 kernel: [    0.000000]   9 disabled
Dec 26 09:04:52 l05 kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 26 09:04:52 l05 kernel: [    0.000000] last_pfn = 0xba000 max_arch_pfn = 0x400000000
Dec 26 09:04:52 l05 kernel: [    0.000000] initial memory mapped : 0 - 20000000
Dec 26 09:04:52 l05 kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 20480
Dec 26 09:04:52 l05 kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000ba000000
Dec 26 09:04:52 l05 kernel: [    0.000000]  0000000000 - 00ba000000 page 2M
Dec 26 09:04:52 l05 kernel: [    0.000000] kernel direct mapping tables up to ba000000 @ 1fffc000-20000000
Dec 26 09:04:52 l05 kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000023ee00000
Dec 26 09:04:52 l05 kernel: [    0.000000]  0100000000 - 023ee00000 page 2M
Dec 26 09:04:52 l05 kernel: [    0.000000] kernel direct mapping tables up to 23ee00000 @ b9fad000-b9fb3000
Dec 26 09:04:52 l05 kernel: [    0.000000] RAMDISK: 35820000 - 36c08000
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: RSDP 00000000000f2f10 00024 (v02 HPQOEM)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: XSDT 00000000b9ffe120 0008C (v01 HPQOEM SLIC-MPC 0000000F      01000013)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: FACP 00000000b9ffc000 0010C (v05 HPQOEM 1815     0000000F HP   00000001)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI Warning: FADT (revision 5) is longer than ACPI 2.0 version, truncating length 268 to 244 (20110623/tbfadt-288)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: DSDT 00000000b9fd4000 22D8D (v02 HPQOEM 1815     00000001 INTL 20110112)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: FACS 00000000b9cf5000 00040
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: HPET 00000000b9ffb000 00038 (v01 HPQOEM 1815     00000001 HP   00000001)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: APIC 00000000b9ffa000 000BC (v01 HPQOEM 1815     00000001 HP   00000001)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: MCFG 00000000b9ff9000 0003C (v01 HPQOEM 1815     00000001 HP   00000001)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: TCPA 00000000b9ff7000 00032 (v02 HPQOEM 1815     00000000 HP   00000001)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: SSDT 00000000b9fd1000 002CA (v01 HPQOEM SataAhci 00001000 INTL 20110112)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: SSDT 00000000b9fd0000 0048A (v01 HPQOEM PtidDevc 00001000 INTL 20110112)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: SLIC 00000000b9fcf000 00176 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: FPDT 00000000b9fcd000 00044 (v01 HPQOEM 1815     00000001 HP   00000001)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: BGRT 00000000b9fcc000 00038 (v00 HPQOEM 1815     00000001 HP   00000001)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: SSDT 00000000b9fcb000 009B6 (v01  PmRef  Cpu0Ist 00003000 INTL 20110112)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: SSDT 00000000b9fca000 00AAD (v01  PmRef    CpuPm 00003000 INTL 20110112)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: ASF! 00000000b9ff8000 000A5 (v32 HPQOEM 1815     00000001 HP   00000001)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 26 09:04:52 l05 kernel: [    0.000000] No NUMA configuration found
Dec 26 09:04:52 l05 kernel: [    0.000000] Faking a node at 0000000000000000-000000023ee00000
Dec 26 09:04:52 l05 kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000023ee00000
Dec 26 09:04:52 l05 kernel: [    0.000000]   NODE_DATA [000000023edfb000 - 000000023edfffff]
Dec 26 09:04:52 l05 kernel: [    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880236400000-ffff88023e3fffff] on node 0
Dec 26 09:04:52 l05 kernel: [    0.000000] Zone PFN ranges:
Dec 26 09:04:52 l05 kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 26 09:04:52 l05 kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec 26 09:04:52 l05 kernel: [    0.000000]   Normal   0x00100000 -> 0x0023ee00
Dec 26 09:04:52 l05 kernel: [    0.000000] Movable zone start PFN for each node
Dec 26 09:04:52 l05 kernel: [    0.000000] early_node_map[7] active PFN ranges
Dec 26 09:04:52 l05 kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Dec 26 09:04:52 l05 kernel: [    0.000000]     0: 0x00000100 -> 0x00020000
Dec 26 09:04:52 l05 kernel: [    0.000000]     0: 0x00020200 -> 0x00040004
Dec 26 09:04:52 l05 kernel: [    0.000000]     0: 0x00040005 -> 0x000b8b9d
Dec 26 09:04:52 l05 kernel: [    0.000000]     0: 0x000b9d40 -> 0x000b9fb3
Dec 26 09:04:52 l05 kernel: [    0.000000]     0: 0x000b9fff -> 0x000ba000
Dec 26 09:04:52 l05 kernel: [    0.000000]     0: 0x00100000 -> 0x0023ee00
Dec 26 09:04:52 l05 kernel: [    0.000000] On node 0 totalpages: 2062749
Dec 26 09:04:52 l05 kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Dec 26 09:04:52 l05 kernel: [    0.000000]   DMA zone: 5 pages reserved
Dec 26 09:04:52 l05 kernel: [    0.000000]   DMA zone: 3912 pages, LIFO batch:0
Dec 26 09:04:52 l05 kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Dec 26 09:04:52 l05 kernel: [    0.000000]   DMA32 zone: 736336 pages, LIFO batch:31
Dec 26 09:04:52 l05 kernel: [    0.000000]   Normal zone: 20408 pages used for memmap
Dec 26 09:04:52 l05 kernel: [    0.000000]   Normal zone: 1285704 pages, LIFO batch:31
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
Dec 26 09:04:52 l05 kernel: [    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 26 09:04:52 l05 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 26 09:04:52 l05 kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Dec 26 09:04:52 l05 kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Dec 26 09:04:52 l05 kernel: [    0.000000] nr_irqs_gsi: 40
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000b8b9d000 - 00000000b9d40000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000b9fb3000 - 00000000b9fc0000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000b9fc0000 - 00000000b9fff000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000ba000000 - 00000000bf200000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000bf200000 - 00000000e0000000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
Dec 26 09:04:52 l05 kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
Dec 26 09:04:52 l05 kernel: [    0.000000] Allocating PCI resources starting at bf200000 (gap: bf200000:20e00000)
Dec 26 09:04:52 l05 kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 26 09:04:52 l05 kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
Dec 26 09:04:52 l05 kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88023ea00000 s83136 r8192 d23360 u262144
Dec 26 09:04:52 l05 kernel: [    0.000000] pcpu-alloc: s83136 r8192 d23360 u262144 alloc=1*2097152
Dec 26 09:04:52 l05 kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7
Dec 26 09:04:52 l05 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2025952
Dec 26 09:04:52 l05 kernel: [    0.000000] Policy zone: Normal
Dec 26 09:04:52 l05 kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-57-generic root=UUID=2e4355ef-517f-478a-be6b-63ce5ab552ea ro quiet splash vt.handoff=7
Dec 26 09:04:52 l05 kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Dec 26 09:04:52 l05 kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Dec 26 09:04:52 l05 kernel: [    0.000000] Checking aperture...
Dec 26 09:04:52 l05 kernel: [    0.000000] No AGP bridge found
Dec 26 09:04:52 l05 kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Dec 26 09:04:52 l05 kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Dec 26 09:04:52 l05 kernel: [    0.000000] Memory: 8016740k/9418752k available (6586k kernel code, 1167756k absent, 234256k reserved, 6619k data, 924k init)
Dec 26 09:04:52 l05 kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Dec 26 09:04:52 l05 kernel: [    0.000000] Hierarchical RCU implementation.
Dec 26 09:04:52 l05 kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Dec 26 09:04:52 l05 kernel: [    0.000000] NR_IRQS:16640 nr_irqs:744 16
Dec 26 09:04:52 l05 kernel: [    0.000000] Extended CMOS year: 2000
Dec 26 09:04:52 l05 kernel: [    0.000000] vt handoff: transparent VT on vt#7
Dec 26 09:04:52 l05 kernel: [    0.000000] Console: colour dummy device 80x25
Dec 26 09:04:52 l05 kernel: [    0.000000] console [tty0] enabled
Dec 26 09:04:52 l05 kernel: [    0.000000] allocated 67108864 bytes of page_cgroup
Dec 26 09:04:52 l05 kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 26 09:04:52 l05 kernel: [    0.000000] hpet clockevent registered
Dec 26 09:04:52 l05 kernel: [    0.000000] Fast TSC calibration failed
Dec 26 09:04:52 l05 kernel: [    0.008000] TSC: PIT calibration matches HPET. 1 loops
Dec 26 09:04:52 l05 kernel: [    0.008000] Detected 2494.082 MHz processor.
Dec 26 09:04:52 l05 kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4988.16 BogoMIPS (lpj=9976328)
Dec 26 09:04:52 l05 kernel: [    0.000007] pid_max: default: 32768 minimum: 301
Dec 26 09:04:52 l05 kernel: [    0.000031] Security Framework initialized
Dec 26 09:04:52 l05 kernel: [    0.000045] AppArmor: AppArmor initialized
Dec 26 09:04:52 l05 kernel: [    0.000047] Yama: becoming mindful.
Dec 26 09:04:52 l05 kernel: [    0.000666] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Dec 26 09:04:52 l05 kernel: [    0.003220] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Dec 26 09:04:52 l05 kernel: [    0.004347] Mount-cache hash table entries: 256
Dec 26 09:04:52 l05 kernel: [    0.004462] Initializing cgroup subsys cpuacct
Dec 26 09:04:52 l05 kernel: [    0.004467] Initializing cgroup subsys memory
Dec 26 09:04:52 l05 kernel: [    0.004476] Initializing cgroup subsys devices
Dec 26 09:04:52 l05 kernel: [    0.004478] Initializing cgroup subsys freezer
Dec 26 09:04:52 l05 kernel: [    0.004480] Initializing cgroup subsys blkio
Dec 26 09:04:52 l05 kernel: [    0.004485] Initializing cgroup subsys perf_event
Dec 26 09:04:52 l05 kernel: [    0.004517] CPU: Physical Processor ID: 0
Dec 26 09:04:52 l05 kernel: [    0.004518] CPU: Processor Core ID: 0
Dec 26 09:04:52 l05 kernel: [    0.004524] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Dec 26 09:04:52 l05 kernel: [    0.004525] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Dec 26 09:04:52 l05 kernel: [    0.004991] mce: CPU supports 7 MCE banks
Dec 26 09:04:52 l05 kernel: [    0.005005] CPU0: Thermal monitoring enabled (TM1)
Dec 26 09:04:52 l05 kernel: [    0.005013] using mwait in idle threads.
Dec 26 09:04:52 l05 kernel: [    0.007944] ACPI: Core revision 20110623
Dec 26 09:04:52 l05 kernel: [    0.071102] ftrace: allocating 26597 entries in 105 pages
Dec 26 09:04:52 l05 kernel: [    0.081856] x2apic not enabled, IRQ remapping init failed
Dec 26 09:04:52 l05 kernel: [    0.082264] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 26 09:04:52 l05 kernel: [    0.121894] CPU0: Intel(R) Core(TM) i7-3667U CPU @ 2.00GHz stepping 09
Dec 26 09:04:52 l05 kernel: [    0.229404] Performance Events: PEBS fmt1+, generic architected perfmon, Intel PMU driver.
Dec 26 09:04:52 l05 kernel: [    0.229410] ... version:                3
Dec 26 09:04:52 l05 kernel: [    0.229412] ... bit width:              48
Dec 26 09:04:52 l05 kernel: [    0.229413] ... generic registers:      4
Dec 26 09:04:52 l05 kernel: [    0.229415] ... value mask:             0000ffffffffffff
Dec 26 09:04:52 l05 kernel: [    0.229416] ... max period:             000000007fffffff
Dec 26 09:04:52 l05 kernel: [    0.229418] ... fixed-purpose events:   3
Dec 26 09:04:52 l05 kernel: [    0.229419] ... event mask:             000000070000000f
Dec 26 09:04:52 l05 kernel: [    0.229576] NMI watchdog enabled, takes one hw-pmu counter.
Dec 26 09:04:52 l05 kernel: [    0.229661] Booting Node   0, Processors  #1
Dec 26 09:04:52 l05 kernel: [    0.229664] smpboot cpu 1: start_ip = 98000
Dec 26 09:04:52 l05 kernel: [    0.337843] NMI watchdog enabled, takes one hw-pmu counter.
Dec 26 09:04:52 l05 kernel: [    0.337939]  #2
Dec 26 09:04:52 l05 kernel: [    0.337941] smpboot cpu 2: start_ip = 98000
Dec 26 09:04:52 l05 kernel: [    0.445717] NMI watchdog enabled, takes one hw-pmu counter.
Dec 26 09:04:52 l05 kernel: [    0.445796]  #3
Dec 26 09:04:52 l05 kernel: [    0.445797] smpboot cpu 3: start_ip = 98000
Dec 26 09:04:52 l05 kernel: [    0.553572] NMI watchdog enabled, takes one hw-pmu counter.
Dec 26 09:04:52 l05 kernel: [    0.553602] Brought up 4 CPUs
Dec 26 09:04:52 l05 kernel: [    0.553604] Total of 4 processors activated (19953.50 BogoMIPS).
Dec 26 09:04:52 l05 kernel: [    0.558630] devtmpfs: initialized
Dec 26 09:04:52 l05 kernel: [    0.559563] EVM: security.selinux
Dec 26 09:04:52 l05 kernel: [    0.559565] EVM: security.SMACK64
Dec 26 09:04:52 l05 kernel: [    0.559566] EVM: security.capability
Dec 26 09:04:52 l05 kernel: [    0.559592] PM: Registering ACPI NVS region at b9fb3000 (53248 bytes)
Dec 26 09:04:52 l05 kernel: [    0.560461] print_constraints: dummy:
Dec 26 09:04:52 l05 kernel: [    0.560493] RTC time: 22:04:42, date: 12/25/13
Dec 26 09:04:52 l05 kernel: [    0.560525] NET: Registered protocol family 16
Dec 26 09:04:52 l05 kernel: [    0.560623] Trying to unpack rootfs image as initramfs...
Dec 26 09:04:52 l05 kernel: [    0.560632] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Dec 26 09:04:52 l05 kernel: [    0.560635] ACPI: bus type pci registered
Dec 26 09:04:52 l05 kernel: [    0.560711] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Dec 26 09:04:52 l05 kernel: [    0.560714] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Dec 26 09:04:52 l05 kernel: [    0.626890] PCI: Using configuration type 1 for base access
Dec 26 09:04:52 l05 kernel: [    0.627892] bio: create slab <bio-0> at 0
Dec 26 09:04:52 l05 kernel: [    0.627982] ACPI: Added _OSI(Module Device)
Dec 26 09:04:52 l05 kernel: [    0.627984] ACPI: Added _OSI(Processor Device)
Dec 26 09:04:52 l05 kernel: [    0.627986] ACPI: Added _OSI(3.0 _SCP Extensions)
Dec 26 09:04:52 l05 kernel: [    0.627988] ACPI: Added _OSI(Processor Aggregator Device)
Dec 26 09:04:52 l05 kernel: [    0.630126] ACPI: EC: Look up EC in DSDT
Dec 26 09:04:52 l05 kernel: [    0.632640] ACPI: Executed 1 blocks of module-level executable AML code
Dec 26 09:04:52 l05 kernel: [    0.652875] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Dec 26 09:04:52 l05 kernel: [    0.801996] ACPI: SSDT 00000000b9cf3018 00861 (v01  PmRef  Cpu0Cst 00003001 INTL 20110112)
Dec 26 09:04:52 l05 kernel: [    0.802539] ACPI: Dynamic OEM Table Load:
Dec 26 09:04:52 l05 kernel: [    0.802542] ACPI: SSDT           (null) 00861 (v01  PmRef  Cpu0Cst 00003001 INTL 20110112)
Dec 26 09:04:52 l05 kernel: [    0.836845] ACPI: SSDT 00000000b9cf4a98 00303 (v01  PmRef    ApIst 00003000 INTL 20110112)
Dec 26 09:04:52 l05 kernel: [    0.837418] ACPI: Dynamic OEM Table Load:
Dec 26 09:04:52 l05 kernel: [    0.837421] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20110112)
Dec 26 09:04:52 l05 kernel: [    0.872649] ACPI: SSDT 00000000b9cf2d98 00119 (v01  PmRef    ApCst 00003000 INTL 20110112)
Dec 26 09:04:52 l05 kernel: [    0.873186] ACPI: Dynamic OEM Table Load:
Dec 26 09:04:52 l05 kernel: [    0.873189] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20110112)
Dec 26 09:04:52 l05 kernel: [    0.962537] Freeing initrd memory: 20384k freed
Dec 26 09:04:52 l05 kernel: [    1.333639] ACPI: Interpreter enabled
Dec 26 09:04:52 l05 kernel: [    1.333645] ACPI: (supports S0 S3 S4 S5)
Dec 26 09:04:52 l05 kernel: [    1.333672] ACPI: Using IOAPIC for interrupt routing
Dec 26 09:04:52 l05 kernel: [    1.335429] ACPI: Power Resource [APPR] (off)
Dec 26 09:04:52 l05 kernel: [    1.353189] ACPI: Power Resource [COMP] (on)
Dec 26 09:04:52 l05 kernel: [    1.353526] ACPI: Power Resource [LPP] (on)
Dec 26 09:04:52 l05 kernel: [    1.355930] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
Dec 26 09:04:52 l05 kernel: [    1.356161] ACPI: No dock devices found.
Dec 26 09:04:52 l05 kernel: [    1.356163] HEST: Table not found.
Dec 26 09:04:52 l05 kernel: [    1.356167] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 26 09:04:52 l05 kernel: [    1.356895] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
Dec 26 09:04:52 l05 kernel: [    1.357482] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Dec 26 09:04:52 l05 kernel: [    1.357485] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Dec 26 09:04:52 l05 kernel: [    1.357488] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Dec 26 09:04:52 l05 kernel: [    1.357491] pci_root PNP0A08:00: host bridge window [mem 0xbf200000-0xdfffffff]
Dec 26 09:04:52 l05 kernel: [    1.357493] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfedfffff]
Dec 26 09:04:52 l05 kernel: [    1.357496] pci_root PNP0A08:00: host bridge window [mem 0xfee01000-0xffffffff]
Dec 26 09:04:52 l05 kernel: [    1.357509] pci 0000:00:00.0: [8086:0154] type 0 class 0x000600
Dec 26 09:04:52 l05 kernel: [    1.357553] pci 0000:00:02.0: [8086:0166] type 0 class 0x000300
Dec 26 09:04:52 l05 kernel: [    1.357566] pci 0000:00:02.0: reg 10: [mem 0xd0000000-0xd03fffff 64bit]
Dec 26 09:04:52 l05 kernel: [    1.357574] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff 64bit pref]
Dec 26 09:04:52 l05 kernel: [    1.357580] pci 0000:00:02.0: reg 20: [io  0x2000-0x203f]
Dec 26 09:04:52 l05 kernel: [    1.357640] pci 0000:00:14.0: [8086:1e31] type 0 class 0x000c03
Dec 26 09:04:52 l05 kernel: [    1.357666] pci 0000:00:14.0: reg 10: [mem 0xd0720000-0xd072ffff 64bit]
Dec 26 09:04:52 l05 kernel: [    1.357743] pci 0000:00:14.0: PME# supported from D3hot D3cold
Dec 26 09:04:52 l05 kernel: [    1.357749] pci 0000:00:14.0: PME# disabled
Dec 26 09:04:52 l05 kernel: [    1.357774] pci 0000:00:16.0: [8086:1e3a] type 0 class 0x000780
Dec 26 09:04:52 l05 kernel: [    1.357800] pci 0000:00:16.0: reg 10: [mem 0xd0734000-0xd073400f 64bit]
Dec 26 09:04:52 l05 kernel: [    1.357884] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Dec 26 09:04:52 l05 kernel: [    1.357888] pci 0000:00:16.0: PME# disabled
Dec 26 09:04:52 l05 bluetoothd[1257]: Failed to init gatt_example plugin
Dec 26 09:04:52 l05 dbus[1180]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Dec 26 09:04:52 l05 kernel: [    1.357914] pci 0000:00:16.3: [8086:1e3d] type 0 class 0x000700
Dec 26 09:04:52 l05 kernel: [    1.357935] pci 0000:00:16.3: reg 10: [io  0x2090-0x2097]
Dec 26 09:04:52 l05 kernel: [    1.357946] pci 0000:00:16.3: reg 14: [mem 0xd073b000-0xd073bfff]
Dec 26 09:04:52 l05 kernel: [    1.358054] pci 0000:00:19.0: [8086:1502] type 0 class 0x000200
Dec 26 09:04:52 l05 kernel: [    1.358075] pci 0000:00:19.0: reg 10: [mem 0xd0700000-0xd071ffff]
Dec 26 09:04:52 l05 kernel: [    1.358085] pci 0000:00:19.0: reg 14: [mem 0xd073a000-0xd073afff]
Dec 26 09:04:52 l05 kernel: [    1.358096] pci 0000:00:19.0: reg 18: [io  0x2060-0x207f]
Dec 26 09:04:52 l05 kernel: [    1.358165] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
Dec 26 09:04:52 l05 kernel: [    1.358170] pci 0000:00:19.0: PME# disabled
Dec 26 09:04:52 l05 kernel: [    1.358195] pci 0000:00:1a.0: [8086:1e2d] type 0 class 0x000c03
Dec 26 09:04:52 l05 kernel: [    1.358219] pci 0000:00:1a.0: reg 10: [mem 0xd0739000-0xd07393ff]
Dec 26 09:04:52 l05 kernel: [    1.358318] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Dec 26 09:04:52 l05 kernel: [    1.358323] pci 0000:00:1a.0: PME# disabled
Dec 26 09:04:52 l05 kernel: [    1.358350] pci 0000:00:1b.0: [8086:1e20] type 0 class 0x000403
Dec 26 09:04:52 l05 kernel: [    1.358368] pci 0000:00:1b.0: reg 10: [mem 0xd0730000-0xd0733fff 64bit]
Dec 26 09:04:52 l05 kernel: [    1.358443] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec 26 09:04:52 l05 kernel: [    1.358448] pci 0000:00:1b.0: PME# disabled
Dec 26 09:04:52 l05 kernel: [    1.358475] pci 0000:00:1c.0: [8086:1e10] type 1 class 0x000604
Dec 26 09:04:52 l05 kernel: [    1.358561] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 26 09:04:52 l05 kernel: [    1.358566] pci 0000:00:1c.0: PME# disabled
Dec 26 09:04:52 l05 kernel: [    1.358595] pci 0000:00:1c.2: [8086:1e14] type 1 class 0x000604
Dec 26 09:04:52 l05 kernel: [    1.358681] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Dec 26 09:04:52 l05 kernel: [    1.358686] pci 0000:00:1c.2: PME# disabled
Dec 26 09:04:52 l05 kernel: [    1.358712] pci 0000:00:1c.3: [8086:1e16] type 1 class 0x000604
Dec 26 09:04:52 l05 kernel: [    1.358798] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Dec 26 09:04:52 l05 kernel: [    1.358803] pci 0000:00:1c.3: PME# disabled
Dec 26 09:04:52 l05 kernel: [    1.358842] pci 0000:00:1d.0: [8086:1e26] type 0 class 0x000c03
Dec 26 09:04:52 l05 kernel: [    1.358866] pci 0000:00:1d.0: reg 10: [mem 0xd0738000-0xd07383ff]
Dec 26 09:04:52 l05 kernel: [    1.358964] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Dec 26 09:04:52 l05 kernel: [    1.358969] pci 0000:00:1d.0: PME# disabled
Dec 26 09:04:52 l05 kernel: [    1.358995] pci 0000:00:1f.0: [8086:1e55] type 0 class 0x000601
Dec 26 09:04:52 l05 kernel: [    1.359130] pci 0000:00:1f.2: [8086:1e03] type 0 class 0x000106
Dec 26 09:04:52 l05 kernel: [    1.359150] pci 0000:00:1f.2: reg 10: [io  0x2088-0x208f]
Dec 26 09:04:52 l05 kernel: [    1.359160] pci 0000:00:1f.2: reg 14: [io  0x209c-0x209f]
Dec 26 09:04:52 l05 kernel: [    1.359169] pci 0000:00:1f.2: reg 18: [io  0x2080-0x2087]
Dec 26 09:04:52 l05 kernel: [    1.359178] pci 0000:00:1f.2: reg 1c: [io  0x2098-0x209b]
Dec 26 09:04:52 l05 kernel: [    1.359187] pci 0000:00:1f.2: reg 20: [io  0x2040-0x205f]
Dec 26 09:04:52 l05 kernel: [    1.359196] pci 0000:00:1f.2: reg 24: [mem 0xd0737000-0xd07377ff]
Dec 26 09:04:52 l05 kernel: [    1.359246] pci 0000:00:1f.2: PME# supported from D3hot
Dec 26 09:04:52 l05 kernel: [    1.359251] pci 0000:00:1f.2: PME# disabled
Dec 26 09:04:52 l05 kernel: [    1.359320] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
Dec 26 09:04:52 l05 kernel: [    1.359328] pci 0000:00:1c.0:   bridge window [mem 0xd0600000-0xd06fffff]
Dec 26 09:04:52 l05 kernel: [    1.359408] pci 0000:02:00.0: [197b:2392] type 0 class 0x000880
Dec 26 09:04:52 l05 kernel: [    1.359437] pci 0000:02:00.0: reg 10: [mem 0xd0503000-0xd05030ff]
Dec 26 09:04:52 l05 kernel: [    1.359548] pci 0000:02:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
Dec 26 09:04:52 l05 kernel: [    1.359700] pci 0000:02:00.2: [197b:2391] type 0 class 0x000805
Dec 26 09:04:52 l05 kernel: [    1.359727] pci 0000:02:00.2: reg 10: [mem 0xd0502000-0xd05020ff]
Dec 26 09:04:52 l05 kernel: [    1.368507] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
Dec 26 09:04:52 l05 kernel: [    1.368515] pci 0000:00:1c.2:   bridge window [mem 0xd0500000-0xd05fffff]
Dec 26 09:04:52 l05 kernel: [    1.368731] pci 0000:03:00.0: [8086:088e] type 0 class 0x000280
Dec 26 09:04:52 l05 kernel: [    1.368897] pci 0000:03:00.0: reg 10: [mem 0xd0400000-0xd0401fff 64bit]
Dec 26 09:04:52 l05 kernel: [    1.369639] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Dec 26 09:04:52 l05 kernel: [    1.369674] pci 0000:03:00.0: PME# disabled
Dec 26 09:04:52 l05 kernel: [    1.376578] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
Dec 26 09:04:52 l05 kernel: [    1.376585] pci 0000:00:1c.3:   bridge window [mem 0xd0400000-0xd04fffff]
Dec 26 09:04:52 l05 kernel: [    1.376612] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 26 09:04:52 l05 kernel: [    1.376787] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Dec 26 09:04:52 l05 kernel: [    1.376821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Dec 26 09:04:52 l05 kernel: [    1.376867] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
Dec 26 09:04:52 l05 kernel: [    1.377316]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Dec 26 09:04:52 l05 kernel: [    1.378482]  pci0000:00: ACPI _OSC control (0x1d) granted
Dec 26 09:04:52 l05 kernel: [    1.383914] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *10 11 12 14 15)
Dec 26 09:04:52 l05 kernel: [    1.383961] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 10 11 12 14 15)
Dec 26 09:04:52 l05 kernel: [    1.384004] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
Dec 26 09:04:52 l05 kernel: [    1.384045] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
Dec 26 09:04:52 l05 kernel: [    1.384087] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
Dec 26 09:04:52 l05 kernel: [    1.384128] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Dec 26 09:04:52 l05 kernel: [    1.384173] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *10 11 12 14 15)
Dec 26 09:04:52 l05 kernel: [    1.384214] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Dec 26 09:04:52 l05 kernel: [    1.384321] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Dec 26 09:04:52 l05 kernel: [    1.384329] vgaarb: loaded
Dec 26 09:04:52 l05 kernel: [    1.384330] vgaarb: bridge control possible 0000:00:02.0
Dec 26 09:04:52 l05 kernel: [    1.384431] i2c-core: driver [aat2870] using legacy suspend method
Dec 26 09:04:52 l05 kernel: [    1.384432] i2c-core: driver [aat2870] using legacy resume method
Dec 26 09:04:52 l05 kernel: [    1.384492] SCSI subsystem initialized
Dec 26 09:04:52 l05 kernel: [    1.384549] libata version 3.00 loaded.
Dec 26 09:04:52 l05 kernel: [    1.384594] usbcore: registered new interface driver usbfs
Dec 26 09:04:52 l05 kernel: [    1.384604] usbcore: registered new interface driver hub
Dec 26 09:04:52 l05 kernel: [    1.384628] usbcore: registered new device driver usb
Dec 26 09:04:52 l05 kernel: [    1.384710] PCI: Using ACPI for IRQ routing
Dec 26 09:04:52 l05 kernel: [    1.391854] PCI: pci_cache_line_size set to 64 bytes
Dec 26 09:04:52 l05 kernel: [    1.391943] reserve RAM buffer: 000000000009dc00 - 000000000009ffff
Dec 26 09:04:52 l05 kernel: [    1.391946] reserve RAM buffer: 0000000040004000 - 0000000043ffffff
Dec 26 09:04:52 l05 kernel: [    1.391948] reserve RAM buffer: 00000000b8b9d000 - 00000000bbffffff
Dec 26 09:04:52 l05 kernel: [    1.391951] reserve RAM buffer: 00000000b9fb3000 - 00000000bbffffff
Dec 26 09:04:52 l05 kernel: [    1.391953] reserve RAM buffer: 00000000ba000000 - 00000000bbffffff
Dec 26 09:04:52 l05 kernel: [    1.391955] reserve RAM buffer: 000000023ee00000 - 000000023fffffff
Dec 26 09:04:52 l05 kernel: [    1.392058] NetLabel: Initializing
Dec 26 09:04:52 l05 kernel: [    1.392059] NetLabel:  domain hash size = 128
Dec 26 09:04:52 l05 kernel: [    1.392061] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 26 09:04:52 l05 kernel: [    1.392071] NetLabel:  unlabeled traffic allowed by default
Dec 26 09:04:52 l05 kernel: [    1.392125] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Dec 26 09:04:52 l05 kernel: [    1.392132] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Dec 26 09:04:52 l05 kernel: [    1.394147] Switching to clocksource hpet
Dec 26 09:04:52 l05 kernel: [    1.400028] AppArmor: AppArmor Filesystem Enabled
Dec 26 09:04:52 l05 kernel: [    1.400053] pnp: PnP ACPI init
Dec 26 09:04:52 l05 kernel: [    1.400065] ACPI: bus type pnp registered
Dec 26 09:04:52 l05 kernel: [    1.400409] pnp 00:00: [bus 00-3e]
Dec 26 09:04:52 l05 kernel: [    1.400412] pnp 00:00: [io  0x0000-0x0cf7 window]
Dec 26 09:04:52 l05 kernel: [    1.400414] pnp 00:00: [io  0x0cf8-0x0cff]
Dec 26 09:04:52 l05 kernel: [    1.400416] pnp 00:00: [io  0x0d00-0xffff window]
Dec 26 09:04:52 l05 kernel: [    1.400418] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Dec 26 09:04:52 l05 kernel: [    1.400420] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Dec 26 09:04:52 l05 kernel: [    1.400422] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Dec 26 09:04:52 l05 kernel: [    1.400424] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Dec 26 09:04:52 l05 kernel: [    1.400427] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Dec 26 09:04:52 l05 kernel: [    1.400429] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Dec 26 09:04:52 l05 kernel: [    1.400431] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Dec 26 09:04:52 l05 kernel: [    1.400433] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Dec 26 09:04:52 l05 kernel: [    1.400435] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Dec 26 09:04:52 l05 kernel: [    1.400437] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Dec 26 09:04:52 l05 kernel: [    1.400439] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Dec 26 09:04:52 l05 kernel: [    1.400441] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Dec 26 09:04:52 l05 kernel: [    1.400443] pnp 00:00: [mem 0x000ec000-0x000effff window]
Dec 26 09:04:52 l05 kernel: [    1.400445] pnp 00:00: [mem 0x000f0000-0x000fffff window]
Dec 26 09:04:52 l05 kernel: [    1.400447] pnp 00:00: [mem 0xbf200000-0xdfffffff window]
Dec 26 09:04:52 l05 kernel: [    1.400451] pnp 00:00: [mem 0xf0000000-0xfedfffff window]
Dec 26 09:04:52 l05 kernel: [    1.400453] pnp 00:00: [mem 0xfee01000-0xffffffff window]
Dec 26 09:04:52 l05 kernel: [    1.400520] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Dec 26 09:04:52 l05 kernel: [    1.400611] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
Dec 26 09:04:52 l05 kernel: [    1.400614] pnp 00:01: [mem 0xfed10000-0xfed17fff]
Dec 26 09:04:52 l05 kernel: [    1.400615] pnp 00:01: [mem 0xfed18000-0xfed18fff]
Dec 26 09:04:52 l05 kernel: [    1.400617] pnp 00:01: [mem 0xfed19000-0xfed19fff]
Dec 26 09:04:52 l05 kernel: [    1.400620] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Dec 26 09:04:52 l05 kernel: [    1.400622] pnp 00:01: [mem 0xe0000000-0xefffffff]
Dec 26 09:04:52 l05 kernel: [    1.400624] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
Dec 26 09:04:52 l05 kernel: [    1.400625] pnp 00:01: [mem 0xfed90000-0xfed93fff]
Dec 26 09:04:52 l05 kernel: [    1.400627] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
Dec 26 09:04:52 l05 kernel: [    1.400629] pnp 00:01: [mem 0xfec00000-0xfec00fff]
Dec 26 09:04:52 l05 kernel: [    1.400672] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.400675] system 00:01: [mem 0xfed10000-0xfed17fff] could not be reserved
Dec 26 09:04:52 l05 kernel: [    1.400678] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.400681] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.400683] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.400686] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.400689] system 00:01: [mem 0xfed90000-0xfed93fff] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.400691] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.400694] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
Dec 26 09:04:52 l05 kernel: [    1.400698] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 26 09:04:52 l05 kernel: [    1.400792] pnp 00:02: [io  0x0000-0x001f]
Dec 26 09:04:52 l05 kernel: [    1.400794] pnp 00:02: [io  0x0081-0x0091]
Dec 26 09:04:52 l05 kernel: [    1.400795] pnp 00:02: [io  0x0093-0x009f]
Dec 26 09:04:52 l05 kernel: [    1.400797] pnp 00:02: [io  0x00c0-0x00df]
Dec 26 09:04:52 l05 kernel: [    1.400799] pnp 00:02: [dma 4]
Dec 26 09:04:52 l05 kernel: [    1.400835] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Dec 26 09:04:52 l05 kernel: [    1.400843] pnp 00:03: [mem 0xff000000-0xffffffff]
Dec 26 09:04:52 l05 kernel: [    1.400874] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
Dec 26 09:04:52 l05 kernel: [    1.400924] pnp 00:04: [io  0xfe00-0xfe0f]
Dec 26 09:04:52 l05 kernel: [    1.400926] pnp 00:04: [io  0xfe80-0xfe8f]
Dec 26 09:04:52 l05 kernel: [    1.400927] pnp 00:04: [mem 0xfed40000-0xfed44fff]
Dec 26 09:04:52 l05 kernel: [    1.400962] pnp 00:04: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
Dec 26 09:04:52 l05 kernel: [    1.401042] pnp 00:05: [mem 0xfed00000-0xfed003ff]
Dec 26 09:04:52 l05 kernel: [    1.401078] pnp 00:05: Plug and Play ACPI device, IDs PNP0103 (active)
Dec 26 09:04:52 l05 kernel: [    1.401087] pnp 00:06: [io  0x00f0]
Dec 26 09:04:52 l05 kernel: [    1.401097] pnp 00:06: [irq 13]
Dec 26 09:04:52 l05 kernel: [    1.401130] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec 26 09:04:52 l05 kernel: [    1.401140] pnp 00:07: [io  0x002e-0x002f]
Dec 26 09:04:52 l05 kernel: [    1.401141] pnp 00:07: [io  0x004e-0x004f]
Dec 26 09:04:52 l05 kernel: [    1.401143] pnp 00:07: [io  0x0061]
Dec 26 09:04:52 l05 kernel: [    1.401145] pnp 00:07: [io  0x0063]
Dec 26 09:04:52 l05 kernel: [    1.401146] pnp 00:07: [io  0x0065]
Dec 26 09:04:52 l05 kernel: [    1.401148] pnp 00:07: [io  0x0067]
Dec 26 09:04:52 l05 kernel: [    1.401149] pnp 00:07: [io  0x0070]
Dec 26 09:04:52 l05 kernel: [    1.401151] pnp 00:07: [io  0x0080]
Dec 26 09:04:52 l05 kernel: [    1.401153] pnp 00:07: [io  0x0092]
Dec 26 09:04:52 l05 kernel: [    1.401154] pnp 00:07: [io  0x00b2-0x00b3]
Dec 26 09:04:52 l05 kernel: [    1.401156] pnp 00:07: [io  0x0200-0x027f]
Dec 26 09:04:52 l05 kernel: [    1.401158] pnp 00:07: [io  0x1000-0x100f]
Dec 26 09:04:52 l05 kernel: [    1.401160] pnp 00:07: [io  0xffff]
Dec 26 09:04:52 l05 kernel: [    1.401161] pnp 00:07: [io  0xffff]
Dec 26 09:04:52 l05 kernel: [    1.401163] pnp 00:07: [io  0x0400-0x047f]
Dec 26 09:04:52 l05 kernel: [    1.401165] pnp 00:07: [io  0x0500-0x057f]
Dec 26 09:04:52 l05 kernel: [    1.401167] pnp 00:07: [io  0xef80-0xef9f]
Dec 26 09:04:52 l05 kernel: [    1.401218] system 00:07: [io  0x0200-0x027f] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.401220] system 00:07: [io  0x1000-0x100f] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.401223] system 00:07: [io  0xffff] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.401225] system 00:07: [io  0xffff] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.401227] system 00:07: [io  0x0400-0x047f] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.401230] system 00:07: [io  0x0500-0x057f] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.401232] system 00:07: [io  0xef80-0xef9f] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.401235] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec 26 09:04:52 l05 kernel: [    1.401243] pnp 00:08: [io  0x0070-0x0077]
Dec 26 09:04:52 l05 kernel: [    1.401250] pnp 00:08: [irq 8]
Dec 26 09:04:52 l05 kernel: [    1.401284] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec 26 09:04:52 l05 kernel: [    1.401651] pnp 00:09: [io  0x03f8-0x03ff]
Dec 26 09:04:52 l05 kernel: [    1.401657] pnp 00:09: [irq 4]
Dec 26 09:04:52 l05 kernel: [    1.401717] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)
Dec 26 09:04:52 l05 kernel: [    1.402049] pnp 00:0a: [io  0x0378-0x037f]
Dec 26 09:04:52 l05 kernel: [    1.402051] pnp 00:0a: [io  0x0778-0x077a]
Dec 26 09:04:52 l05 kernel: [    1.402057] pnp 00:0a: [irq 5]
Dec 26 09:04:52 l05 kernel: [    1.402059] pnp 00:0a: [dma 0 disabled]
Dec 26 09:04:52 l05 kernel: [    1.402164] pnp 00:0a: Plug and Play ACPI device, IDs PNP0401 (active)
Dec 26 09:04:52 l05 kernel: [    1.402174] pnp 00:0b: [io  0x0060]
Dec 26 09:04:52 l05 kernel: [    1.402175] pnp 00:0b: [io  0x0064]
Dec 26 09:04:52 l05 kernel: [    1.402181] pnp 00:0b: [irq 1]
Dec 26 09:04:52 l05 kernel: [    1.402218] pnp 00:0b: Plug and Play ACPI device, IDs HPQ8001 PNP0303 (active)
Dec 26 09:04:52 l05 kernel: [    1.402229] pnp 00:0c: [irq 12]
Dec 26 09:04:52 l05 kernel: [    1.402267] pnp 00:0c: Plug and Play ACPI device, IDs SYN0192 SYN0100 SYN0002 PNP0f13 (active)
Dec 26 09:04:52 l05 kernel: [    1.402484] pnp 00:0d: [irq 23]
Dec 26 09:04:52 l05 kernel: [    1.402528] pnp 00:0d: Plug and Play ACPI device, IDs HPQ6000 (active)
Dec 26 09:04:52 l05 kernel: [    1.402567] pnp 00:0e: [mem 0x20000000-0x201fffff]
Dec 26 09:04:52 l05 kernel: [    1.402569] pnp 00:0e: [mem 0x40004000-0x40004fff]
Dec 26 09:04:52 l05 kernel: [    1.402625] system 00:0e: [mem 0x20000000-0x201fffff] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.402628] system 00:0e: [mem 0x40004000-0x40004fff] has been reserved
Dec 26 09:04:52 l05 kernel: [    1.402631] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec 26 09:04:52 l05 kernel: [    1.402814] pnp: PnP ACPI: found 15 devices
Dec 26 09:04:52 l05 kernel: [    1.402816] ACPI: ACPI bus type pnp unregistered
Dec 26 09:04:52 l05 kernel: [    1.409305] pci 0000:02:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
Dec 26 09:04:52 l05 kernel: [    1.409310] PCI: max bus depth: 1 pci_try_num: 2
Dec 26 09:04:52 l05 kernel: [    1.409344] pci 0000:00:1c.2: BAR 15: assigned [mem 0xbf200000-0xbf2fffff pref]
Dec 26 09:04:52 l05 kernel: [    1.409347] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
Dec 26 09:04:52 l05 kernel: [    1.409353] pci 0000:00:1c.0:   bridge window [mem 0xd0600000-0xd06fffff]
Dec 26 09:04:52 l05 kernel: [    1.409364] pci 0000:02:00.0: BAR 6: assigned [mem 0xbf200000-0xbf20ffff pref]
Dec 26 09:04:52 l05 kernel: [    1.409367] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
Dec 26 09:04:52 l05 kernel: [    1.409372] pci 0000:00:1c.2:   bridge window [mem 0xd0500000-0xd05fffff]
Dec 26 09:04:52 l05 kernel: [    1.409377] pci 0000:00:1c.2:   bridge window [mem 0xbf200000-0xbf2fffff pref]
Dec 26 09:04:52 l05 kernel: [    1.409385] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
Dec 26 09:04:52 l05 kernel: [    1.409391] pci 0000:00:1c.3:   bridge window [mem 0xd0400000-0xd04fffff]
Dec 26 09:04:52 l05 kernel: [    1.409414] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 26 09:04:52 l05 kernel: [    1.409420] pci 0000:00:1c.0: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    1.409431] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 26 09:04:52 l05 kernel: [    1.409436] pci 0000:00:1c.2: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    1.409446] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Dec 26 09:04:52 l05 kernel: [    1.409451] pci 0000:00:1c.3: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    1.409456] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Dec 26 09:04:52 l05 kernel: [    1.409458] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Dec 26 09:04:52 l05 kernel: [    1.409461] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Dec 26 09:04:52 l05 kernel: [    1.409463] pci_bus 0000:00: resource 7 [mem 0xbf200000-0xdfffffff]
Dec 26 09:04:52 l05 kernel: [    1.409465] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xfedfffff]
Dec 26 09:04:52 l05 kernel: [    1.409467] pci_bus 0000:00: resource 9 [mem 0xfee01000-0xffffffff]
Dec 26 09:04:52 l05 kernel: [    1.409470] pci_bus 0000:01: resource 1 [mem 0xd0600000-0xd06fffff]
Dec 26 09:04:52 l05 kernel: [    1.409472] pci_bus 0000:02: resource 1 [mem 0xd0500000-0xd05fffff]
Dec 26 09:04:52 l05 kernel: [    1.409475] pci_bus 0000:02: resource 2 [mem 0xbf200000-0xbf2fffff pref]
Dec 26 09:04:52 l05 kernel: [    1.409477] pci_bus 0000:03: resource 1 [mem 0xd0400000-0xd04fffff]
Dec 26 09:04:52 l05 kernel: [    1.409507] NET: Registered protocol family 2
Dec 26 09:04:52 l05 kernel: [    1.409693] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec 26 09:04:52 l05 kernel: [    1.410489] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Dec 26 09:04:52 l05 kernel: [    1.411739] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec 26 09:04:52 l05 kernel: [    1.411867] TCP: Hash tables configured (established 524288 bind 65536)
Dec 26 09:04:52 l05 kernel: [    1.411869] TCP reno registered
Dec 26 09:04:52 l05 kernel: [    1.411884] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Dec 26 09:04:52 l05 kernel: [    1.411920] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Dec 26 09:04:52 l05 kernel: [    1.412014] NET: Registered protocol family 1
Dec 26 09:04:52 l05 kernel: [    1.412027] pci 0000:00:02.0: Boot video device
Dec 26 09:04:52 l05 kernel: [    1.412037] pci 0000:00:14.0: enabling device (0000 -> 0002)
Dec 26 09:04:52 l05 kernel: [    1.412043] pci 0000:00:14.0: can't derive routing for PCI INT A
Dec 26 09:04:52 l05 kernel: [    1.412045] pci 0000:00:14.0: PCI INT A: no GSI - using ISA IRQ 10
Dec 26 09:04:52 l05 kernel: [    1.412121] pci 0000:00:14.0: can't derive routing for PCI INT A
Dec 26 09:04:52 l05 kernel: [    1.412145] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 26 09:04:52 l05 kernel: [    1.412178] pci 0000:00:1a.0: PCI INT A disabled
Dec 26 09:04:52 l05 kernel: [    1.412199] pci 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 26 09:04:52 l05 kernel: [    1.412224] pci 0000:00:1d.0: PCI INT A disabled
Dec 26 09:04:52 l05 kernel: [    1.412245] PCI: CLS 64 bytes, default 64
Dec 26 09:04:52 l05 kernel: [    1.412247] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Dec 26 09:04:52 l05 kernel: [    1.412249] Placing 64MB software IO TLB between ffff8800b4b9d000 - ffff8800b8b9d000
Dec 26 09:04:52 l05 kernel: [    1.412251] software IO TLB at phys 0xb4b9d000 - 0xb8b9d000
Dec 26 09:04:52 l05 kernel: [    1.412750] audit: initializing netlink socket (disabled)
Dec 26 09:04:52 l05 kernel: [    1.412763] type=2000 audit(1388009082.200:1): initialized
Dec 26 09:04:52 l05 kernel: [    1.441156] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 26 09:04:52 l05 kernel: [    1.443246] VFS: Disk quotas dquot_6.5.2
Dec 26 09:04:52 l05 kernel: [    1.443299] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec 26 09:04:52 l05 kernel: [    1.443745] fuse init (API version 7.17)
Dec 26 09:04:52 l05 kernel: [    1.443829] msgmni has been set to 15697
Dec 26 09:04:52 l05 kernel: [    1.444183] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 26 09:04:52 l05 kernel: [    1.444210] io scheduler noop registered
Dec 26 09:04:52 l05 kernel: [    1.444212] io scheduler deadline registered
Dec 26 09:04:52 l05 kernel: [    1.444242] io scheduler cfq registered (default)
Dec 26 09:04:52 l05 kernel: [    1.444332] pcieport 0000:00:1c.0: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    1.444385] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [    1.444460] pcieport 0000:00:1c.2: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    1.444505] pcieport 0000:00:1c.2: irq 41 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [    1.444579] pcieport 0000:00:1c.3: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    1.444623] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [    1.444716] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
Dec 26 09:04:52 l05 kernel: [    1.444722] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
Dec 26 09:04:52 l05 kernel: [    1.444741] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
Dec 26 09:04:52 l05 kernel: [    1.444743] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Dec 26 09:04:52 l05 kernel: [    1.444745] pci 0000:02:00.2: Signaling PME through PCIe PME interrupt
Dec 26 09:04:52 l05 kernel: [    1.444750] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
Dec 26 09:04:52 l05 kernel: [    1.444768] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
Dec 26 09:04:52 l05 kernel: [    1.444770] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Dec 26 09:04:52 l05 kernel: [    1.444775] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
Dec 26 09:04:52 l05 kernel: [    1.444790] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 26 09:04:52 l05 kernel: [    1.444809] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 26 09:04:52 l05 kernel: [    1.444857] intel_idle: MWAIT substates: 0x21120
Dec 26 09:04:52 l05 kernel: [    1.444859] intel_idle: v0.4 model 0x3A
Dec 26 09:04:52 l05 kernel: [    1.444860] intel_idle: lapic_timer_reliable_states 0xffffffff
Dec 26 09:04:52 l05 kernel: [    1.445005] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Dec 26 09:04:52 l05 kernel: [    1.445106] ACPI: AC Adapter [AC] (on-line)
Dec 26 09:04:52 l05 kernel: [    1.445309] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Dec 26 09:04:52 l05 kernel: [    1.445314] ACPI: Sleep Button [SLPB]
Dec 26 09:04:52 l05 kernel: [    1.445353] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Dec 26 09:04:52 l05 kernel: [    1.445377] ACPI: Lid Switch [LID]
Dec 26 09:04:52 l05 kernel: [    1.445414] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Dec 26 09:04:52 l05 kernel: [    1.445418] ACPI: Power Button [PWRF]
Dec 26 09:04:52 l05 kernel: [    1.466635] thermal LNXTHERM:00: registered as thermal_zone0
Dec 26 09:04:52 l05 kernel: [    1.466638] ACPI: Thermal Zone [CPUZ] (44 C)
Dec 26 09:04:52 l05 kernel: [    1.485520] thermal LNXTHERM:01: registered as thermal_zone1
Dec 26 09:04:52 l05 kernel: [    1.485523] ACPI: Thermal Zone [GFXZ] (0 C)
Dec 26 09:04:52 l05 kernel: [    1.495418] thermal LNXTHERM:02: registered as thermal_zone2
Dec 26 09:04:52 l05 kernel: [    1.495420] ACPI: Thermal Zone [EXTZ] (45 C)
Dec 26 09:04:52 l05 kernel: [    1.505347] thermal LNXTHERM:03: registered as thermal_zone3
Dec 26 09:04:52 l05 kernel: [    1.505349] ACPI: Thermal Zone [LOCZ] (25 C)
Dec 26 09:04:52 l05 kernel: [    1.515293] thermal LNXTHERM:04: registered as thermal_zone4
Dec 26 09:04:52 l05 kernel: [    1.515295] ACPI: Thermal Zone [BATZ] (24 C)
Dec 26 09:04:52 l05 kernel: [    1.515568] thermal LNXTHERM:05: registered as thermal_zone5
Dec 26 09:04:52 l05 kernel: [    1.515570] ACPI: Thermal Zone [PCHZ] (127 C)
Dec 26 09:04:52 l05 kernel: [    1.515647] thermal LNXTHERM:06: registered as thermal_zone6
Dec 26 09:04:52 l05 kernel: [    1.515648] ACPI: Thermal Zone [DM1Z] (0 C)
Dec 26 09:04:52 l05 kernel: [    1.515721] thermal LNXTHERM:07: registered as thermal_zone7
Dec 26 09:04:52 l05 kernel: [    1.515723] ACPI: Thermal Zone [DM2Z] (0 C)
Dec 26 09:04:52 l05 kernel: [    1.515748] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
Dec 26 09:04:52 l05 kernel: [    1.515755] ACPI: Battery Slot [BAT0] (battery present)
Dec 26 09:04:52 l05 kernel: [    1.515781] ERST: Table is not found!
Dec 26 09:04:52 l05 kernel: [    1.515782] GHES: HEST is not enabled!
Dec 26 09:04:52 l05 kernel: [    1.515862] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Dec 26 09:04:52 l05 kernel: [    1.536554] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 26 09:04:52 l05 kernel: [    1.559167] ACPI: Battery Slot [BAT0] (battery present)
Dec 26 09:04:52 l05 kernel: [    1.686709] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 26 09:04:52 l05 kernel: [    1.686826] serial 0000:00:16.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 26 09:04:52 l05 kernel: [    1.707074] 0000:00:16.3: ttyS4 at I/O 0x2090 (irq = 17) is a 16550A
Dec 26 09:04:52 l05 kernel: [    1.721938] Linux agpgart interface v0.103
Dec 26 09:04:52 l05 kernel: [    1.722022] agpgart-intel 0000:00:00.0: Intel Ivybridge Chipset
Dec 26 09:04:52 l05 kernel: [    1.722176] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
Dec 26 09:04:52 l05 kernel: [    1.723853] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
Dec 26 09:04:52 l05 kernel: [    1.723973] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
Dec 26 09:04:52 l05 kernel: [    1.725206] brd: module loaded
Dec 26 09:04:52 l05 kernel: [    1.725875] loop: module loaded
Dec 26 09:04:52 l05 kernel: [    1.725990] ahci 0000:00:1f.2: version 3.0
Dec 26 09:04:52 l05 kernel: [    1.726002] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 26 09:04:52 l05 kernel: [    1.726052] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [    1.726080] ahci: SSS flag set, parallel bus scan disabled
Dec 26 09:04:52 l05 kernel: [    1.741694] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x29 impl SATA mode
Dec 26 09:04:52 l05 kernel: [    1.741698] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems sxs apst
Dec 26 09:04:52 l05 kernel: [    1.741704] ahci 0000:00:1f.2: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    1.758080] scsi0 : ahci
Dec 26 09:04:52 l05 kernel: [    1.758160] scsi1 : ahci
Dec 26 09:04:52 l05 kernel: [    1.758226] scsi2 : ahci
Dec 26 09:04:52 l05 kernel: [    1.758295] scsi3 : ahci
Dec 26 09:04:52 l05 kernel: [    1.758359] scsi4 : ahci
Dec 26 09:04:52 l05 kernel: [    1.758423] scsi5 : ahci
Dec 26 09:04:52 l05 kernel: [    1.758655] ata1: SATA max UDMA/133 abar m2048@0xd0737000 port 0xd0737100 irq 43
Dec 26 09:04:52 l05 kernel: [    1.758657] ata2: DUMMY
Dec 26 09:04:52 l05 kernel: [    1.758658] ata3: DUMMY
Dec 26 09:04:52 l05 kernel: [    1.758662] ata4: SATA max UDMA/133 abar m2048@0xd0737000 port 0xd0737280 irq 43
Dec 26 09:04:52 l05 kernel: [    1.758663] ata5: DUMMY
Dec 26 09:04:52 l05 kernel: [    1.758667] ata6: SATA max UDMA/133 abar m2048@0xd0737000 port 0xd0737380 irq 43
Dec 26 09:04:52 l05 kernel: [    1.759018] Fixed MDIO Bus: probed
Dec 26 09:04:52 l05 kernel: [    1.759035] tun: Universal TUN/TAP device driver, 1.6
Dec 26 09:04:52 l05 kernel: [    1.759037] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 26 09:04:52 l05 kernel: [    1.759079] PPP generic driver version 2.4.2
Dec 26 09:04:52 l05 kernel: [    1.759165] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 26 09:04:52 l05 kernel: [    1.759179] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 26 09:04:52 l05 kernel: [    1.759196] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    1.759200] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Dec 26 09:04:52 l05 kernel: [    1.759240] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec 26 09:04:52 l05 kernel: [    1.759265] ehci_hcd 0000:00:1a.0: debug port 2
Dec 26 09:04:52 l05 kernel: [    1.763157] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
Dec 26 09:04:52 l05 kernel: [    1.763173] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xd0739000
Dec 26 09:04:52 l05 kernel: [    1.777629] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Dec 26 09:04:52 l05 kernel: [    1.777744] hub 1-0:1.0: USB hub found
Dec 26 09:04:52 l05 kernel: [    1.777748] hub 1-0:1.0: 3 ports detected
Dec 26 09:04:52 l05 kernel: [    1.777807] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 26 09:04:52 l05 kernel: [    1.777823] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    1.777826] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Dec 26 09:04:52 l05 kernel: [    1.777865] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Dec 26 09:04:52 l05 kernel: [    1.777887] ehci_hcd 0000:00:1d.0: debug port 2
Dec 26 09:04:52 l05 kernel: [    1.781777] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
Dec 26 09:04:52 l05 kernel: [    1.781782] ehci_hcd 0000:00:1d.0: irq 16, io mem 0xd0738000
Dec 26 09:04:52 l05 kernel: [    1.797602] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Dec 26 09:04:52 l05 kernel: [    1.797703] hub 2-0:1.0: USB hub found
Dec 26 09:04:52 l05 kernel: [    1.797706] hub 2-0:1.0: 3 ports detected
Dec 26 09:04:52 l05 kernel: [    1.797764] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 26 09:04:52 l05 kernel: [    1.797774] uhci_hcd: USB Universal Host Controller Interface driver
Dec 26 09:04:52 l05 kernel: [    1.797799] xhci_hcd 0000:00:14.0: can't derive routing for PCI INT A
Dec 26 09:04:52 l05 kernel: [    1.797801] xhci_hcd 0000:00:14.0: PCI INT A: no GSI - using ISA IRQ 10
Dec 26 09:04:52 l05 kernel: [    1.797835] xhci_hcd 0000:00:14.0: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    1.797839] xhci_hcd 0000:00:14.0: xHCI Host Controller
Dec 26 09:04:52 l05 kernel: [    1.797877] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
Dec 26 09:04:52 l05 kernel: [    1.797966] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
Dec 26 09:04:52 l05 kernel: [    1.798011] xhci_hcd 0000:00:14.0: irq 44 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [    1.798119] xHCI xhci_add_endpoint called for root hub
Dec 26 09:04:52 l05 kernel: [    1.798122] xHCI xhci_check_bandwidth called for root hub
Dec 26 09:04:52 l05 kernel: [    1.798143] hub 3-0:1.0: USB hub found
Dec 26 09:04:52 l05 kernel: [    1.798150] hub 3-0:1.0: 4 ports detected
Dec 26 09:04:52 l05 kernel: [    1.798202] xhci_hcd 0000:00:14.0: xHCI Host Controller
Dec 26 09:04:52 l05 kernel: [    1.798235] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
Dec 26 09:04:52 l05 kernel: [    1.798311] xHCI xhci_add_endpoint called for root hub
Dec 26 09:04:52 l05 kernel: [    1.798313] xHCI xhci_check_bandwidth called for root hub
Dec 26 09:04:52 l05 kernel: [    1.798334] hub 4-0:1.0: USB hub found
Dec 26 09:04:52 l05 kernel: [    1.798341] hub 4-0:1.0: 4 ports detected
Dec 26 09:04:52 l05 kernel: [    1.865544] usbcore: registered new interface driver libusual
Dec 26 09:04:52 l05 kernel: [    1.865585] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 26 09:04:52 l05 kernel: [    1.867408] i8042: Detected active multiplexing controller, rev 1.1
Dec 26 09:04:52 l05 kernel: [    1.868171] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 26 09:04:52 l05 kernel: [    1.868177] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec 26 09:04:52 l05 kernel: [    1.868185] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec 26 09:04:52 l05 kernel: [    1.868189] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec 26 09:04:52 l05 kernel: [    1.868192] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec 26 09:04:52 l05 kernel: [    1.868291] mousedev: PS/2 mouse device common for all mice
Dec 26 09:04:52 l05 kernel: [    1.868467] rtc_cmos 00:08: RTC can wake from S4
Dec 26 09:04:52 l05 kernel: [    1.868580] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Dec 26 09:04:52 l05 kernel: [    1.868616] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Dec 26 09:04:52 l05 kernel: [    1.868699] device-mapper: uevent: version 1.0.3
Dec 26 09:04:52 l05 kernel: [    1.868772] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
Dec 26 09:04:52 l05 kernel: [    1.868887] cpuidle: using governor ladder
Dec 26 09:04:52 l05 kernel: [    1.869057] cpuidle: using governor menu
Dec 26 09:04:52 l05 kernel: [    1.869059] EFI Variables Facility v0.08 2004-May-17
Dec 26 09:04:52 l05 kernel: [    1.869250] TCP cubic registered
Dec 26 09:04:52 l05 kernel: [    1.869358] NET: Registered protocol family 10
Dec 26 09:04:52 l05 kernel: [    1.869754] NET: Registered protocol family 17
Dec 26 09:04:52 l05 kernel: [    1.869759] Registering the dns_resolver key type
Dec 26 09:04:52 l05 kernel: [    1.869909] PM: Hibernation image not present or could not be loaded.
Dec 26 09:04:52 l05 kernel: [    1.869919] registered taskstats version 1
Dec 26 09:04:52 l05 kernel: [    1.876795]   Magic number: 9:763:98
Dec 26 09:04:52 l05 kernel: [    1.876893] rtc_cmos 00:08: setting system clock to 2013-12-25 22:04:43 UTC (1388009083)
Dec 26 09:04:52 l05 kernel: [    1.877619] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 26 09:04:52 l05 kernel: [    1.877620] EDD information not available.
Dec 26 09:04:52 l05 kernel: [    1.889506] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Dec 26 09:04:52 l05 kernel: [    2.009413] usb 4-1: new SuperSpeed USB device number 2 using xhci_hcd
Dec 26 09:04:52 l05 kernel: [    2.026190] hub 4-1:1.0: USB hub found
Dec 26 09:04:52 l05 kernel: [    2.026219] hub 4-1:1.0: 4 ports detected
Dec 26 09:04:52 l05 kernel: [    2.077240] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Dec 26 09:04:52 l05 kernel: [    2.077596] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Dec 26 09:04:52 l05 kernel: [    2.077599] ata1.00: supports DRM functions and may not be fully accessible
Dec 26 09:04:52 l05 kernel: [    2.077715] ata1.00: ATA-9: MTFDDAK256MAM-1K12, 07TA, max UDMA/100
Dec 26 09:04:52 l05 kernel: [    2.077724] ata1.00: 500118192 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
Dec 26 09:04:52 l05 kernel: [    2.078228] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Dec 26 09:04:52 l05 kernel: [    2.078231] ata1.00: supports DRM functions and may not be fully accessible
Dec 26 09:04:52 l05 kernel: [    2.078331] ata1.00: configured for UDMA/100
Dec 26 09:04:52 l05 kernel: [    2.078626] scsi 0:0:0:0: Direct-Access     ATA      MTFDDAK256MAM-1K 07TA PQ: 0 ANSI: 5
Dec 26 09:04:52 l05 kernel: [    2.078745] sd 0:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
Dec 26 09:04:52 l05 kernel: [    2.078772] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 26 09:04:52 l05 kernel: [    2.078860] sd 0:0:0:0: [sda] Write Protect is off
Dec 26 09:04:52 l05 kernel: [    2.078863] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 26 09:04:52 l05 kernel: [    2.078888] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 26 09:04:52 l05 kernel: [    2.080218]  sda: sda1 sda3 < sda5 >
Dec 26 09:04:52 l05 kernel: [    2.080859] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 26 09:04:52 l05 kernel: [    2.137191] usb 1-1: new high-speed USB device number 2 using ehci_hcd
Dec 26 09:04:52 l05 kernel: [    2.269813] hub 1-1:1.0: USB hub found
Dec 26 09:04:52 l05 kernel: [    2.270004] hub 1-1:1.0: 6 ports detected
Dec 26 09:04:52 l05 kernel: [    2.380858] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Dec 26 09:04:52 l05 kernel: [    2.396855] ata4: SATA link down (SStatus 0 SControl 300)
Dec 26 09:04:52 l05 kernel: [    2.408826] Refined TSC clocksource calibration: 2494.333 MHz.
Dec 26 09:04:52 l05 kernel: [    2.408837] Switching to clocksource tsc
Dec 26 09:04:52 l05 kernel: [    2.513359] hub 2-1:1.0: USB hub found
Dec 26 09:04:52 l05 kernel: [    2.513557] hub 2-1:1.0: 8 ports detected
Dec 26 09:04:52 l05 kernel: [    2.680489] usb 3-1: new high-speed USB device number 2 using xhci_hcd
Dec 26 09:04:52 l05 kernel: [    2.697223] hub 3-1:1.0: USB hub found
Dec 26 09:04:52 l05 kernel: [    2.697247] hub 3-1:1.0: 4 ports detected
Dec 26 09:04:52 l05 kernel: [    2.716431] ata6: SATA link down (SStatus 0 SControl 300)
Dec 26 09:04:52 l05 kernel: [    2.717441] Freeing unused kernel memory: 924k freed
Dec 26 09:04:52 l05 kernel: [    2.717521] Write protecting the kernel read-only data: 12288k
Dec 26 09:04:52 l05 kernel: [    2.720443] Freeing unused kernel memory: 1588k freed
Dec 26 09:04:52 l05 kernel: [    2.722735] Freeing unused kernel memory: 1188k freed
Dec 26 09:04:52 l05 kernel: [    2.751654] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
Dec 26 09:04:52 l05 kernel: [    2.751656] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
Dec 26 09:04:52 l05 kernel: [    2.751683] e1000e 0000:00:19.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 26 09:04:52 l05 kernel: [    2.751694] e1000e 0000:00:19.0: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    2.751807] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [    2.756491] [drm] Initialized drm 1.1.0 20060810
Dec 26 09:04:52 l05 kernel: [    2.762641] sdhci: Secure Digital Host Controller Interface driver
Dec 26 09:04:52 l05 kernel: [    2.762644] sdhci: Copyright(c) Pierre Ossman
Dec 26 09:04:52 l05 kernel: [    2.762898] sdhci-pci 0000:02:00.0: SDHCI controller found [197b:2392] (rev 30)
Dec 26 09:04:52 l05 kernel: [    2.762919] sdhci-pci 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 26 09:04:52 l05 kernel: [    2.762963] sdhci-pci 0000:02:00.0: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    2.762987] mmc0: no vmmc regulator found
Dec 26 09:04:52 l05 kernel: [    2.763024] Registered led device: mmc0::
Dec 26 09:04:52 l05 kernel: [    2.764061] mmc0: SDHCI controller on PCI [0000:02:00.0] using DMA
Dec 26 09:04:52 l05 kernel: [    2.764077] sdhci-pci 0000:02:00.2: SDHCI controller found [197b:2391] (rev 30)
Dec 26 09:04:52 l05 kernel: [    2.764093] sdhci-pci 0000:02:00.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Dec 26 09:04:52 l05 kernel: [    2.764098] sdhci-pci 0000:02:00.2: Refusing to bind to secondary interface.
Dec 26 09:04:52 l05 kernel: [    2.764106] sdhci-pci 0000:02:00.2: PCI INT A disabled
Dec 26 09:04:52 l05 kernel: [    2.771594] wmi: Mapper loaded
Dec 26 09:04:52 l05 kernel: [    2.864241] usb 3-2: new full-speed USB device number 3 using xhci_hcd
Dec 26 09:04:52 l05 kernel: [    2.889063] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input4
Dec 26 09:04:52 l05 kernel: [    2.889239] generic-usb 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:14.0-2/input0
Dec 26 09:04:52 l05 kernel: [    2.894696] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.1/input/input5
Dec 26 09:04:52 l05 kernel: [    2.894903] generic-usb 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:14.0-2/input1
Dec 26 09:04:52 l05 kernel: [    2.909224] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.2/input/input6
Dec 26 09:04:52 l05 kernel: [    2.909402] generic-usb 0003:045E:0745.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:14.0-2/input2
Dec 26 09:04:52 l05 kernel: [    2.909417] usbcore: registered new interface driver usbhid
Dec 26 09:04:52 l05 kernel: [    2.909419] usbhid: USB HID core driver
Dec 26 09:04:52 l05 kernel: [    2.949466] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 10:1f:74:77:1b:e1
Dec 26 09:04:52 l05 kernel: [    2.949469] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Dec 26 09:04:52 l05 kernel: [    2.949519] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
Dec 26 09:04:52 l05 kernel: [    2.949578] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 26 09:04:52 l05 kernel: [    2.949583] i915 0000:00:02.0: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [    2.956174] usb 1-1.1: new full-speed USB device number 3 using ehci_hcd
Dec 26 09:04:52 l05 kernel: [    3.000001] i915 0000:00:02.0: irq 46 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [    3.000013] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Dec 26 09:04:52 l05 kernel: [    3.000015] [drm] Driver supports precise vblank timestamp query.
Dec 26 09:04:52 l05 kernel: [    3.000076] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed
Dec 26 09:04:52 l05 kernel: [    3.000592] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Dec 26 09:04:52 l05 kernel: [    3.025066] mmc0: new SDHC card at address e624
Dec 26 09:04:52 l05 kernel: [    3.026195] mmcblk0: mmc0:e624 SU32G 29.7 GiB
Dec 26 09:04:52 l05 kernel: [    3.031314]  mmcblk0: p1
Dec 26 09:04:52 l05 kernel: [    3.124124] usb 1-1.2: new full-speed USB device number 4 using ehci_hcd
Dec 26 09:04:52 l05 kernel: [    3.291929] usb 1-1.3: new high-speed USB device number 5 using ehci_hcd
Dec 26 09:04:52 l05 kernel: [    3.669142] fbcon: inteldrmfb (fb0) is primary device
Dec 26 09:04:52 l05 kernel: [    3.669183] Console: switching to colour frame buffer device 170x48
Dec 26 09:04:52 l05 kernel: [    3.669198] fb0: inteldrmfb frame buffer device
Dec 26 09:04:52 l05 kernel: [    3.669199] drm: registered panic notifier
Dec 26 09:04:52 l05 kernel: [    3.749113] acpi device:0b: registered as cooling_device4
Dec 26 09:04:52 l05 kernel: [    3.749355] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
Dec 26 09:04:52 l05 kernel: [    3.749415] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Dec 26 09:04:52 l05 kernel: [    3.749449] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Dec 26 09:04:52 l05 kernel: [    3.755209] usb 1-1.5: new high-speed USB device number 6 using ehci_hcd
Dec 26 09:04:52 l05 kernel: [    3.950830] [drm] Changing LVDS panel from (+hsync, +vsync) to (+hsync, -vsync)
Dec 26 09:04:52 l05 kernel: [    3.970918] usb 3-1.4: new low-speed USB device number 4 using xhci_hcd
Dec 26 09:04:52 l05 kernel: [    3.990679] usb 3-1.4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
Dec 26 09:04:52 l05 kernel: [    3.990686] usb 3-1.4: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
Dec 26 09:04:52 l05 kernel: [    3.993293] input: HID 1017:0002 as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.4/3-1.4:1.0/input/input8
Dec 26 09:04:52 l05 kernel: [    3.993512] generic-usb 0003:1017:0002.0004: input,hidraw3: USB HID v1.00 Keyboard [HID 1017:0002] on usb-0000:00:14.0-1.4/input0
Dec 26 09:04:52 l05 kernel: [    3.998092] input: HID 1017:0002 as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1.4/3-1.4:1.1/input/input9
Dec 26 09:04:52 l05 kernel: [    3.998382] generic-usb 0003:1017:0002.0005: input,hidraw4: USB HID v1.00 Mouse [HID 1017:0002] on usb-0000:00:14.0-1.4/input1
Dec 26 09:04:52 l05 kernel: [    9.959456] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Dec 26 09:04:52 l05 kernel: [   10.205410] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 26 09:04:52 l05 kernel: [   10.240789] lp: driver loaded but no devices found
Dec 26 09:04:52 l05 kernel: [   10.264812] mei: module is from the staging directory, the quality is unknown, you have been warned.
Dec 26 09:04:52 l05 kernel: [   10.265127] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 26 09:04:52 l05 kernel: [   10.265134] mei 0000:00:16.0: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [   10.265193] mei 0000:00:16.0: irq 47 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [   10.268525] hp_accel: laptop model unknown, using default axes configuration
Dec 26 09:04:52 l05 kernel: [   10.269146] lis3lv02d: 8 bits 3DC sensor found
Dec 26 09:04:52 l05 kernel: [   10.286297] tpm_tis 00:04: 1.2 TPM (device-id 0xB, rev-id 16)
Dec 26 09:04:52 l05 kernel: [   10.310645] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input10
Dec 26 09:04:52 l05 kernel: [   10.310819] Registered led device: hp::hddprotect
Dec 26 09:04:52 l05 kernel: [   10.310851] hp_accel: driver loaded
Dec 26 09:04:52 l05 kernel: [   10.318472] cfg80211: Calling CRDA to update world regulatory domain
Dec 26 09:04:52 l05 kernel: [   10.332405] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Dec 26 09:04:52 l05 kernel: [   10.332408] Copyright(c) 2003-2011 Intel Corporation
Dec 26 09:04:52 l05 kernel: [   10.332452] iwlwifi 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 26 09:04:52 l05 kernel: [   10.332463] iwlwifi 0000:03:00.0: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [   10.333348] type=1400 audit(1388009091.962:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=702 comm="apparmor_parser"
Dec 26 09:04:52 l05 kernel: [   10.333698] type=1400 audit(1388009091.962:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=702 comm="apparmor_parser"
Dec 26 09:04:52 l05 kernel: [   10.333901] type=1400 audit(1388009091.962:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=702 comm="apparmor_parser"
Dec 26 09:04:52 l05 kernel: [   10.335078] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
Dec 26 09:04:52 l05 kernel: [   10.335081] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900117f4000
Dec 26 09:04:52 l05 kernel: [   10.335083] iwlwifi 0000:03:00.0: HW Revision ID = 0x24
Dec 26 09:04:52 l05 kernel: [   10.335175] iwlwifi 0000:03:00.0: irq 48 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [   10.335211] iwlwifi 0000:03:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
Dec 26 09:04:52 l05 kernel: [   10.335911] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
Dec 26 09:04:52 l05 kernel: [   10.352061] iwlwifi 0000:03:00.0: device EEPROM VER=0x756, CALIB=0x6
Dec 26 09:04:52 l05 kernel: [   10.352065] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
Dec 26 09:04:52 l05 kernel: [   10.352067] iwlwifi 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
Dec 26 09:04:52 l05 kernel: [   10.353069] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Dec 26 09:04:52 l05 kernel: [   10.393625] Linux video capture interface: v2.00
Dec 26 09:04:52 l05 kernel: [   10.394426] uvcvideo: Found UVC 1.00 device HP HD Webcam [Fixed] (05c8:0340)
Dec 26 09:04:52 l05 kernel: [   10.400979] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
Dec 26 09:04:52 l05 kernel: [   10.400987] snd_hda_intel 0000:00:1b.0: power state changed by ACPI to D0
Dec 26 09:04:52 l05 kernel: [   10.401008] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Dec 26 09:04:52 l05 kernel: [   10.401073] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [   10.401101] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
Dec 26 09:04:52 l05 kernel: [   10.411714] input: HP HD Webcam [Fixed] as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input11
Dec 26 09:04:52 l05 kernel: [   10.411801] usbcore: registered new interface driver uvcvideo
Dec 26 09:04:52 l05 kernel: [   10.411803] USB Video Class driver (1.1.1)
Dec 26 09:04:52 l05 kernel: [   10.431793] cdc_acm 1-1.5:1.1: ttyACM0: USB ACM device
Dec 26 09:04:52 l05 kernel: [   10.433842] cdc_acm 1-1.5:1.3: ttyACM1: USB ACM device
Dec 26 09:04:52 l05 kernel: [   10.441177] cdc_acm 1-1.5:1.9: ttyACM2: USB ACM device
Dec 26 09:04:52 l05 kernel: [   10.445170] usbcore: registered new interface driver cdc_acm
Dec 26 09:04:52 l05 kernel: [   10.445173] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
Dec 26 09:04:52 l05 kernel: [   10.445381] cdc_wdm 1-1.5:1.5: cdc-wdm0: USB WDM device
Dec 26 09:04:52 l05 kernel: [   10.445449] cdc_wdm 1-1.5:1.8: cdc-wdm1: USB WDM device
Dec 26 09:04:52 l05 kernel: [   10.445482] usbcore: registered new interface driver cdc_wdm
Dec 26 09:04:52 l05 kernel: [   10.461220] cdc_ncm: 04-Aug-2011
Dec 26 09:04:52 l05 kernel: [   10.470452] Bluetooth: Core ver 2.16
Dec 26 09:04:52 l05 kernel: [   10.470489] NET: Registered protocol family 31
Dec 26 09:04:52 l05 kernel: [   10.470491] Bluetooth: HCI device and connection manager initialized
Dec 26 09:04:52 l05 kernel: [   10.470493] Bluetooth: HCI socket layer initialized
Dec 26 09:04:52 l05 kernel: [   10.470494] Bluetooth: L2CAP socket layer initialized
Dec 26 09:04:52 l05 kernel: [   10.470499] Bluetooth: SCO socket layer initialized
Dec 26 09:04:52 l05 kernel: [   10.471060] Bluetooth: Generic Bluetooth USB driver ver 0.6
Dec 26 09:04:52 l05 kernel: [   10.472351] usbcore: registered new interface driver btusb
Dec 26 09:04:52 l05 kernel: [   10.473564] ppdev: user-space parallel port driver
Dec 26 09:04:52 l05 kernel: [   10.478002] cfg80211: World regulatory domain updated:
Dec 26 09:04:52 l05 kernel: [   10.478004] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 26 09:04:52 l05 kernel: [   10.478007] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 26 09:04:52 l05 kernel: [   10.478009] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 26 09:04:52 l05 kernel: [   10.478011] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 26 09:04:52 l05 kernel: [   10.478014] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 26 09:04:52 l05 kernel: [   10.478016] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 26 09:04:52 l05 kernel: [   10.478285] usb 1-1.5: MAC-Address: 0x02:0x15:0xe0:0xec:0x01:0x00
Dec 26 09:04:52 l05 kernel: [   10.478648] cdc_ncm 1-1.5:1.6: usb0: register 'cdc_ncm' at usb-0000:00:1a.0-1.5, CDC NCM, 02:15:e0:ec:01:00
Dec 26 09:04:52 l05 kernel: [   10.478667] usbcore: registered new interface driver cdc_ncm
Dec 26 09:04:52 l05 kernel: [   10.481372] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
Dec 26 09:04:52 l05 kernel: [   10.481565] Registered led device: phy0-led
Dec 26 09:04:52 l05 kernel: [   10.481591] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Dec 26 09:04:52 l05 kernel: [   10.489374] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Dec 26 09:04:52 l05 kernel: [   10.766332] input: HP WMI hotkeys as /devices/virtual/input/input12
Dec 26 09:04:52 l05 kernel: [   10.896540] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Dec 26 09:04:52 l05 kernel: [   10.957297] RPC: Registered named UNIX socket transport module.
Dec 26 09:04:52 l05 kernel: [   10.957300] RPC: Registered udp transport module.
Dec 26 09:04:52 l05 kernel: [   10.957302] RPC: Registered tcp transport module.
Dec 26 09:04:52 l05 kernel: [   10.957303] RPC: Registered tcp NFSv4.1 backchannel transport module.
Dec 26 09:04:52 l05 kernel: [   10.959298] FS-Cache: Loaded
Dec 26 09:04:52 l05 kernel: [   10.970079] init: failsafe main process (1130) killed by TERM signal
Dec 26 09:04:52 l05 kernel: [   10.971205] FS-Cache: Netfs 'nfs' registered for caching
Dec 26 09:04:52 l05 kernel: [   10.978225] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Dec 26 09:04:52 l05 kernel: [   10.978284] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Dec 26 09:04:52 l05 kernel: [   10.980915] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Dec 26 09:04:52 l05 kernel: [   10.981776] HDMI: detected monitor SAMSUNG at connection type HDMI
Dec 26 09:04:52 l05 kernel: [   10.981779] HDMI: available speakers: FL/FR
Dec 26 09:04:52 l05 kernel: [   10.981783] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
Dec 26 09:04:52 l05 kernel: [   10.981900] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Dec 26 09:04:52 l05 kernel: [   10.981944] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Dec 26 09:04:52 l05 kernel: [   10.985443] HDMI: detected monitor SAMSUNG at connection type HDMI
Dec 26 09:04:52 l05 kernel: [   10.985446] HDMI: available speakers: FL/FR
Dec 26 09:04:52 l05 kernel: [   10.985450] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
Dec 26 09:04:52 l05 kernel: [   10.985603] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Dec 26 09:04:52 l05 kernel: [   10.990204] HDMI: detected monitor SAMSUNG at connection type HDMI
Dec 26 09:04:52 l05 kernel: [   10.990207] HDMI: available speakers: FL/FR
Dec 26 09:04:52 l05 kernel: [   10.990211] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
Dec 26 09:04:52 l05 kernel: [   10.990271] HDMI status: Codec=3 Pin=6 Presence_Detect=0 ELD_Valid=0
Dec 26 09:04:52 l05 kernel: [   10.991007] HDMI status: Codec=3 Pin=7 Presence_Detect=0 ELD_Valid=0
Dec 26 09:04:52 l05 kernel: [   10.991086] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
Dec 26 09:04:52 l05 kernel: [   10.991279] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
Dec 26 09:04:52 l05 kernel: [   10.991365] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
Dec 26 09:04:52 l05 kernel: [   10.991432] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
Dec 26 09:04:52 l05 kernel: [   10.991491] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
Dec 26 09:04:52 l05 kernel: [   10.991556] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
Dec 26 09:04:52 l05 kernel: [   10.991611] input: HDA Intel PCH Dock Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input19
Dec 26 09:04:52 l05 kernel: [   11.002091] parport_pc 00:0a: reported by Plug and Play ACPI
Dec 26 09:04:52 l05 kernel: [   11.002182] parport0: PC-style at 0x378 (0x778), irq 5, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Dec 26 09:04:52 l05 kernel: [   11.035132] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec 26 09:04:52 l05 kernel: [   11.035135] Bluetooth: BNEP filters: protocol multicast
Dec 26 09:04:52 l05 rpc.statd[1310]: Version 1.2.5 starting
Dec 26 09:04:52 l05 rpc.statd[1310]: Flags: TI-RPC
Dec 26 09:04:52 l05 kernel: [   11.045195] Bluetooth: RFCOMM TTY layer initialized
Dec 26 09:04:52 l05 kernel: [   11.045199] Bluetooth: RFCOMM socket layer initialized
Dec 26 09:04:52 l05 kernel: [   11.045201] Bluetooth: RFCOMM ver 1.11
Dec 26 09:04:52 l05 avahi-daemon[1321]: Found user 'avahi' (UID 107) and group 'avahi' (GID 118).
Dec 26 09:04:52 l05 avahi-daemon[1321]: Successfully dropped root privileges.
Dec 26 09:04:52 l05 avahi-daemon[1321]: avahi-daemon 0.6.30 starting up.
Dec 26 09:04:52 l05 avahi-daemon[1321]: Successfully called chroot().
Dec 26 09:04:52 l05 avahi-daemon[1321]: Successfully dropped remaining capabilities.
Dec 26 09:04:52 l05 polkitd[1295]: started daemon version 0.104 using authority implementation `local' version `0.104'
Dec 26 09:04:52 l05 dbus[1180]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Dec 26 09:04:52 l05 avahi-daemon[1321]: Loading service file /services/udisks.service.
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: init!
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: update_system_hostname
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPluginIfupdown: management mode: unmanaged
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0)
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6/net/usb0, iface: usb0)
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6/net/usb0, iface: usb0): no ifupdown configuration found.
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlan0, iface: wlan0)
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: end _init.
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Dec 26 09:04:52 l05 NetworkManager[1271]:    Ifupdown: get unmanaged devices count: 0
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: (21480608) ... get_connections.
Dec 26 09:04:52 l05 NetworkManager[1271]:    SCPlugin-Ifupdown: (21480608) ... get_connections (managed=false): return empty list.
Dec 26 09:04:52 l05 NetworkManager[1271]:    keyfile: parsing Auto Ethernet ...
Dec 26 09:04:52 l05 NetworkManager[1271]:    keyfile:     read connection 'Auto Ethernet'
Dec 26 09:04:52 l05 NetworkManager[1271]:    keyfile: parsing wlan0101 ...
Dec 26 09:04:52 l05 avahi-daemon[1321]: Network interface enumeration completed.
Dec 26 09:04:52 l05 avahi-daemon[1321]: Registering HINFO record with values 'X86_64'/'LINUX'.
Dec 26 09:04:52 l05 avahi-daemon[1321]: Server startup complete. Host name is l05.local. Local service cookie is 2358497826.
Dec 26 09:04:52 l05 avahi-daemon[1321]: Service "l05" (/services/udisks.service) successfully established.
Dec 26 09:04:52 l05 modem-manager[1240]: <info>  (ttyS4) opening serial port...
Dec 26 09:04:52 l05 modem-manager[1240]: <info>  (ttyACM0) opening serial port...
Dec 26 09:04:52 l05 NetworkManager[1271]:    keyfile:     read connection 'wlan0101'
Dec 26 09:04:52 l05 NetworkManager[1271]:    Ifupdown: get unmanaged devices count: 0
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> modem-manager is now available
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/ieee80211/phy0/rfkill1) (driver (unknown))
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/platform/hp-wmi/rfkill/rfkill2) (driver hp-wmi)
Dec 26 09:04:52 l05 modem-manager[1240]: <info>  (ttyACM1) opening serial port...
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> Networking is enabled by state file
Dec 26 09:04:52 l05 NetworkManager[1271]: <warn> failed to allocate link cache: (-10) Operation not supported
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (eth0): carrier is OFF
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (eth0): new Ethernet device (driver: 'e1000e' ifindex: 2)
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (eth0): now managed
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (eth0): bringing up device.
Dec 26 09:04:52 l05 kernel: [   11.067686] type=1400 audit(1388009092.698:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1373 comm="apparmor_parser"
Dec 26 09:04:52 l05 kernel: [   11.067740] type=1400 audit(1388009092.698:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1374 comm="apparmor_parser"
Dec 26 09:04:52 l05 kernel: [   11.067927] type=1400 audit(1388009092.698:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1373 comm="apparmor_parser"
Dec 26 09:04:52 l05 kernel: [   11.068105] type=1400 audit(1388009092.698:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1374 comm="apparmor_parser"
Dec 26 09:04:52 l05 kernel: [   11.068293] type=1400 audit(1388009092.698:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1374 comm="apparmor_parser"
Dec 26 09:04:52 l05 modem-manager[1240]: <info>  (ttyACM2) opening serial port...
Dec 26 09:04:52 l05 kernel: [   11.071355] type=1400 audit(1388009092.702:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1378 comm="apparmor_parser"
Dec 26 09:04:52 l05 kernel: [   11.071644] type=1400 audit(1388009092.702:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1379 comm="apparmor_parser"
Dec 26 09:04:52 l05 kernel: [   11.076639] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input20
Dec 26 09:04:52 l05 udev-configure-printer: add /devices/pnp0/00:0a/printer/lp0
Dec 26 09:04:52 l05 udev-configure-printer: Failed to get parent
Dec 26 09:04:52 l05 kernel: [   11.089817] lp0: using parport0 (interrupt-driven).
Dec 26 09:04:52 l05 cron[1434]: (CRON) INFO (pidfile fd = 3)
Dec 26 09:04:52 l05 anacron[1450]: Anacron 2.3 started on 2013-12-26
Dec 26 09:04:52 l05 acpid: starting up with proc fs
Dec 26 09:04:52 l05 acpid: 35 rules loaded
Dec 26 09:04:52 l05 acpid: waiting for events: event logging is off
Dec 26 09:04:52 l05 cron[1454]: (CRON) STARTUP (fork ok)
Dec 26 09:04:52 l05 cron[1454]: (CRON) INFO (Running @reboot jobs)
Dec 26 09:04:52 l05 anacron[1450]: Will run job `cron.daily' in 5 min.
Dec 26 09:04:52 l05 anacron[1450]: Jobs will be executed sequentially
Dec 26 09:04:52 l05 kernel: [   11.174449] vboxdrv: Found 4 processor cores.
Dec 26 09:04:52 l05 dbus[1180]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Dec 26 09:04:52 l05 dbus[1180]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Dec 26 09:04:52 l05 kernel: [   11.193556] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [   11.201588] hp_wmi: unknown device type 0x3
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (eth0): preparing device.
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (eth0): deactivating device (reason 'managed') [2]
Dec 26 09:04:52 l05 NetworkManager[1271]: <warn> failed to allocate link cache: (-10) Operation not supported
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (usb0): carrier is OFF
Dec 26 09:04:52 l05 NetworkManager[1271]: <error> [1388009092.886332] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (usb0): unable to read permanent MAC address (error 0)
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (usb0): new Ethernet device (driver: 'cdc_ncm' ifindex: 3)
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (usb0): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (usb0): now managed
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (usb0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (usb0): bringing up device.
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (usb0): preparing device.
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (usb0): deactivating device (reason 'managed') [2]
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (wlan0): using nl80211 for WiFi device control
Dec 26 09:04:52 l05 NetworkManager[1271]: <warn> (wlan0): driver supports Access Point (AP) mode
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 4)
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (wlan0): now managed
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 26 09:04:52 l05 kernel: [   11.249396] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Dec 26 09:04:52 l05 kernel: [   11.249883] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 26 09:04:52 l05 kernel: [   11.250154] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 26 09:04:52 l05 kernel: [   11.251744] ADDRCONF(NETDEV_UP): usb0: link is not ready
Dec 26 09:04:52 l05 kernel: [   11.251930] ADDRCONF(NETDEV_UP): usb0: link is not ready
Dec 26 09:04:52 l05 kernel: [   11.252859] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
Dec 26 09:04:52 l05 kernel: [   11.257744] cdc_ncm: usb0: network connection: disconnected
Dec 26 09:04:52 l05 NetworkManager[1271]: <info> (wlan0): bringing up device.
Dec 26 09:04:52 l05 kernel: [   11.259257] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
Dec 26 09:04:52 l05 acpid: client connected from 1491[0:0]
Dec 26 09:04:52 l05 acpid: 1 client rule loaded
Dec 26 09:04:53 l05 bluetoothd[1257]: Listening for HCI events on hci0
Dec 26 09:04:53 l05 bluetoothd[1257]: HCI dev 0 up
Dec 26 09:04:53 l05 kernel: [   11.458016] vboxdrv: fAsync=0 offMin=0xf1 offMax=0xa63
Dec 26 09:04:53 l05 kernel: [   11.458077] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Dec 26 09:04:53 l05 kernel: [   11.458079] vboxdrv: Successfully loaded version 4.3.4 (interface 0x001a0005).
Dec 26 09:04:53 l05 bluetoothd[1257]: Adapter /org/bluez/1257/hci0 has been enabled
Dec 26 09:04:53 l05 bluetoothd[1257]: Inquiry Cancel Failed with status 0x0c
Dec 26 09:04:53 l05 kernel: [   11.554461] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
Dec 26 09:04:53 l05 kernel: [   11.560876] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
Dec 26 09:04:53 l05 NetworkManager[1271]: <info> (wlan0): preparing device.
Dec 26 09:04:53 l05 NetworkManager[1271]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 26 09:04:53 l05 kernel: [   11.663175] vboxpci: IOMMU not found (not registered)
Dec 26 09:04:53 l05 kernel: [   11.664347] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 26 09:04:53 l05 kernel: [   11.664598] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 26 09:04:53 l05 dbus[1180]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Dec 26 09:04:53 l05 NetworkManager[1271]: <info> found WWAN radio killswitch rfkill3 (at /sys/devices/platform/hp-wmi/rfkill/rfkill3) (driver hp-wmi)
Dec 26 09:04:53 l05 dbus[1180]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Dec 26 09:04:53 l05 NetworkManager[1271]: <info> wpa_supplicant started
Dec 26 09:04:53 l05 NetworkManager[1271]: <info> (wlan0): supplicant interface state: starting -> ready
Dec 26 09:04:53 l05 NetworkManager[1271]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 26 09:04:53 l05 NetworkManager[1271]: <info> (wlan0): supplicant interface state: ready -> inactive
Dec 26 09:04:53 l05 NetworkManager[1271]: <warn> Trying to remove a non-existant call id.
Dec 26 09:04:53 l05 kernel: [   12.004316] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1c0b1, caps: 0xf00133/0x640000/0xa2400
Dec 26 09:04:53 l05 kernel: [   12.038752] Adding 8250364k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:8250364k SS
Dec 26 09:04:53 l05 kernel: [   12.048043] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input21
Dec 26 09:04:54 l05 kernel: [   12.399958] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1
Dec 26 09:04:54 l05 kernel: [   12.400011] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Dec 26 09:04:54 l05 modem-manager[1240]: <info>  (ttyACM0) closing serial port...
Dec 26 09:04:54 l05 modem-manager[1240]: <info>  (ttyACM0) serial port closed
Dec 26 09:04:54 l05 modem-manager[1240]: <info>  (ttyACM0) opening serial port...
Dec 26 09:04:54 l05 modem-manager[1240]: <info>  (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5 claimed port ttyACM0
Dec 26 09:04:54 l05 modem-manager[1240]: <info>  (ttyACM1) closing serial port...
Dec 26 09:04:54 l05 modem-manager[1240]: <info>  (ttyACM1) serial port closed
Dec 26 09:04:54 l05 modem-manager[1240]: <info>  (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5 claimed port ttyACM1
Dec 26 09:04:54 l05 modem-manager[1240]: <info>  (ttyACM2) closing serial port...
Dec 26 09:04:54 l05 modem-manager[1240]: <info>  (ttyACM2) serial port closed
Dec 26 09:04:54 l05 modem-manager[1240]: <info>  (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5 claimed port ttyACM2
Dec 26 09:04:54 l05 kernel: [   12.591682] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Dec 26 09:04:54 l05 kernel: [   12.591719] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Dec 26 09:04:54 l05 kernel: [   12.891273] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Dec 26 09:04:54 l05 kernel: [   12.894788] HDMI: detected monitor SAMSUNG at connection type HDMI
Dec 26 09:04:54 l05 kernel: [   12.894789] HDMI: available speakers: FL/FR
Dec 26 09:04:54 l05 kernel: [   12.894792] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
Dec 26 09:04:54 l05 kernel: [   12.899902] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 17000000, was 12000000
Dec 26 09:04:54 l05 dbus[1180]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Dec 26 09:04:54 l05 dbus[1180]: [system] Successfully activated service 'org.freedesktop.Accounts'
Dec 26 09:04:54 l05 accounts-daemon[1826]: started daemon version 0.6.15
Dec 26 09:04:54 l05 dbus[1180]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Dec 26 09:04:54 l05 dbus[1180]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Dec 26 09:04:55 l05 dbus[1180]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Dec 26 09:04:55 l05 dbus[1180]: [system] Successfully activated service 'org.freedesktop.UPower'
Dec 26 09:04:55 l05 dbus[1180]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Dec 26 09:04:55 l05 dbus[1180]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Successfully called chroot.
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Successfully dropped privileges.
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Successfully limited resources.
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Running.
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Watchdog thread running.
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Successfully made thread 2100 of process 2100 (n/a) owned by '104' high priority at nice level -11.
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Supervising 1 threads of 1 processes of 1 users.
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Canary thread running.
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Successfully made thread 2139 of process 2100 (n/a) owned by '104' RT at priority 5.
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Supervising 2 threads of 1 processes of 1 users.
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Successfully made thread 2143 of process 2100 (n/a) owned by '104' RT at priority 5.
Dec 26 09:04:55 l05 rtkit-daemon[2102]: Supervising 3 threads of 1 processes of 1 users.
Dec 26 09:04:55 l05 bluetoothd[1257]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/HFPAG
Dec 26 09:04:55 l05 bluetoothd[1257]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/A2DPSource
Dec 26 09:04:55 l05 bluetoothd[1257]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/A2DPSink
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> (eth0): carrier now ON (device state 20)
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Auto-activating connection 'Auto Ethernet'.
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) starting connection 'Auto Ethernet'
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 26 09:04:56 l05 kernel: [   14.866452] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Dec 26 09:04:56 l05 kernel: [   14.866912] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> dhclient started with pid 2238
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 26 09:04:56 l05 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Dec 26 09:04:56 l05 dhclient: Copyright 2004-2011 Internet Systems Consortium.
Dec 26 09:04:56 l05 dhclient: All rights reserved.
Dec 26 09:04:56 l05 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Dec 26 09:04:56 l05 dhclient:
Dec 26 09:04:56 l05 NetworkManager[1271]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec 26 09:04:56 l05 dhclient: Listening on LPF/eth0/10:1f:74:77:1b:e1
Dec 26 09:04:56 l05 dhclient: Sending on   LPF/eth0/10:1f:74:77:1b:e1
Dec 26 09:04:56 l05 dhclient: Sending on   Socket/fallback
Dec 26 09:04:56 l05 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 26 09:04:56 l05 dhclient: DHCPREQUEST of 192.168.0.2 on eth0 to 255.255.255.255 port 67
Dec 26 09:04:56 l05 dhclient: DHCPOFFER of 192.168.0.2 from 192.168.0.1
Dec 26 09:04:57 l05 dhclient: DHCPACK of 192.168.0.2 from 192.168.0.1
Dec 26 09:04:57 l05 dhclient: bound to 192.168.0.2 -- renewal in 1704 seconds.
Dec 26 09:04:57 l05 NetworkManager[1271]: <info> (eth0): DHCPv4 state changed preinit -> bound
Dec 26 09:04:57 l05 NetworkManager[1271]: <info>   address 192.168.0.2
Dec 26 09:04:57 l05 NetworkManager[1271]: <info>   prefix 24 (255.255.255.0)
Dec 26 09:04:57 l05 NetworkManager[1271]: <info>   gateway 192.168.0.1
Dec 26 09:04:57 l05 NetworkManager[1271]: <info>   nameserver '61.9.194.49'
Dec 26 09:04:57 l05 NetworkManager[1271]: <info>   nameserver '61.9.195.193'
Dec 26 09:04:57 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 26 09:04:57 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Dec 26 09:04:57 l05 avahi-daemon[1321]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.2.
Dec 26 09:04:57 l05 avahi-daemon[1321]: New relevant interface eth0.IPv4 for mDNS.
Dec 26 09:04:57 l05 avahi-daemon[1321]: Registering new address record for 192.168.0.2 on eth0.IPv4.
Dec 26 09:04:57 l05 avahi-daemon[1321]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::121f:74ff:fe77:1be1.
Dec 26 09:04:57 l05 avahi-daemon[1321]: New relevant interface eth0.IPv6 for mDNS.
Dec 26 09:04:57 l05 avahi-daemon[1321]: Registering new address record for fe80::121f:74ff:fe77:1be1 on eth0.*.
Dec 26 09:04:58 l05 NetworkManager[1271]: <info> DNS: starting dnsmasq...
Dec 26 09:04:58 l05 NetworkManager[1271]: <error> [1388009098.553368] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
Dec 26 09:04:58 l05 NetworkManager[1271]: <error> [1388009098.553385] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Dec 26 09:04:58 l05 NetworkManager[1271]: <warn> DNS: plugin dnsmasq update failed
Dec 26 09:04:58 l05 NetworkManager[1271]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 26 09:04:58 l05 dnsmasq[2245]: started, version 2.59 cache disabled
Dec 26 09:04:58 l05 dnsmasq[2245]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Dec 26 09:04:58 l05 dnsmasq[2245]: DBus support enabled: connected to system bus
Dec 26 09:04:58 l05 dnsmasq[2245]: warning: no upstream servers configured
Dec 26 09:04:58 l05 NetworkManager[1271]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 26 09:04:58 l05 NetworkManager[1271]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS.
Dec 26 09:04:58 l05 NetworkManager[1271]: <info> Activation (eth0) successful, device activated.
Dec 26 09:04:58 l05 NetworkManager[1271]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Dec 26 09:04:58 l05 dbus[1180]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec 26 09:04:58 l05 NetworkManager[1271]: <warn> dnsmasq appeared on DBus: :1.36
Dec 26 09:04:58 l05 NetworkManager[1271]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Dec 26 09:04:58 l05 dnsmasq[2245]: setting upstream servers from DBus
Dec 26 09:04:58 l05 dnsmasq[2245]: using nameserver 61.9.195.193#53
Dec 26 09:04:58 l05 dnsmasq[2245]: using nameserver 61.9.194.49#53
Dec 26 09:04:58 l05 dbus[1180]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 26 09:05:03 l05 modem-manager[1240]: <info>  (ttyACM0) closing serial port...
Dec 26 09:05:03 l05 modem-manager[1240]: <info>  (ttyACM0) serial port closed
Dec 26 09:05:03 l05 NetworkManager[1271]: <warn> (ttyACM0): failed to look up interface index
Dec 26 09:05:03 l05 NetworkManager[1271]: <info> (ttyACM0): new GSM/UMTS device (driver: 'cdc_acm' ifindex: 0)
Dec 26 09:05:03 l05 NetworkManager[1271]: <info> (ttyACM0): exported as /org/freedesktop/NetworkManager/Devices/3
Dec 26 09:05:03 l05 NetworkManager[1271]: <info> (ttyACM0): now managed
Dec 26 09:05:03 l05 NetworkManager[1271]: <info> (ttyACM0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 26 09:05:03 l05 NetworkManager[1271]: <info> (ttyACM0): deactivating device (reason 'managed') [2]
Dec 26 09:05:03 l05 NetworkManager[1271]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Dec 26 09:05:03 l05 NetworkManager[1271]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Dec 26 09:05:03 l05 NetworkManager[1271]: <info> (ttyACM0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
Dec 26 09:05:04 l05 modem-manager[1240]: <info>  (ttyS4) closing serial port...
Dec 26 09:05:04 l05 modem-manager[1240]: <info>  (ttyS4) serial port closed
Dec 26 09:05:04 l05 modem-manager[1240]: <info>  (ttyS4) opening serial port...
Dec 26 09:05:07 l05 kernel: [   25.359134] eth0: no IPv6 routers present
Dec 26 09:05:07 l05 ntpdate[2357]: adjust time server 91.189.94.4 offset 0.397607 sec
Dec 26 09:05:08 l05 lightdm: pam_ecryptfs: Passphrase file wrapped
Dec 26 09:05:09 l05 kernel: [   27.915848] CIFS VFS: default security mechanism requested.  The default security mechanism will be upgraded from ntlm to ntlmv2 in kernel release 3.3
Dec 26 09:05:09 l05 kernel: [   27.980845] CIFS VFS: cifs_mount failed w/return code = -6
Dec 26 09:05:09 l05 kernel: [   28.037975] CIFS VFS: cifs_mount failed w/return code = -6
Dec 26 09:05:09 l05 kernel: [   28.097284] CIFS VFS: cifs_mount failed w/return code = -6
Dec 26 09:05:09 l05 kernel: [   28.154679] CIFS VFS: cifs_mount failed w/return code = -6
Dec 26 09:05:09 l05 kernel: [   28.333554] CIFS VFS: cifs_mount failed w/return code = -6
Dec 26 09:05:09 l05 kernel: [   28.334788] CIFS VFS: cifs_mount failed w/return code = -6
Dec 26 09:05:10 l05 kernel: [   28.403742] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1
Dec 26 09:05:10 l05 kernel: [   28.403814] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
Dec 26 09:05:10 l05 kernel: [   28.745725] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Dec 26 09:05:10 l05 kernel: [   28.745769] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Dec 26 09:05:10 l05 kernel: [   29.044962] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
Dec 26 09:05:10 l05 kernel: [   29.048460] HDMI: detected monitor SAMSUNG at connection type HDMI
Dec 26 09:05:10 l05 kernel: [   29.048463] HDMI: available speakers: FL/FR
Dec 26 09:05:10 l05 kernel: [   29.048467] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000, bits = 16 20 24
Dec 26 09:05:10 l05 modem-manager[1240]: <info>  (ttyS4) closing serial port...
Dec 26 09:05:10 l05 modem-manager[1240]: <info>  (ttyS4) serial port closed
Dec 26 09:05:11 l05 dbus[1180]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Dec 26 09:05:11 l05 dbus[1180]: [system] Successfully activated service 'org.freedesktop.UDisks'
Dec 26 09:05:11 l05 rtkit-daemon[2102]: Successfully made thread 2926 of process 2926 (n/a) owned by '1000' high priority at nice level -11.
Dec 26 09:05:11 l05 rtkit-daemon[2102]: Supervising 4 threads of 2 processes of 2 users.
Dec 26 09:05:12 l05 rtkit-daemon[2102]: Successfully made thread 2936 of process 2926 (n/a) owned by '1000' RT at priority 5.
Dec 26 09:05:12 l05 rtkit-daemon[2102]: Supervising 5 threads of 2 processes of 2 users.
Dec 26 09:05:12 l05 rtkit-daemon[2102]: Successfully made thread 2937 of process 2926 (n/a) owned by '1000' RT at priority 5.
Dec 26 09:05:12 l05 rtkit-daemon[2102]: Supervising 6 threads of 2 processes of 2 users.
Dec 26 09:05:12 l05 bluetoothd[1257]: Endpoint registered: sender=:1.52 path=/MediaEndpoint/HFPAG
Dec 26 09:05:12 l05 bluetoothd[1257]: Endpoint registered: sender=:1.52 path=/MediaEndpoint/A2DPSource
Dec 26 09:05:12 l05 bluetoothd[1257]: Endpoint registered: sender=:1.52 path=/MediaEndpoint/A2DPSink
Dec 26 09:05:12 l05 kernel: [   31.166464] EXT4-fs (mmcblk0p1): warning: maximal mount count reached, running e2fsck is recommended
Dec 26 09:05:12 l05 kernel: [   31.176891] EXT4-fs (mmcblk0p1): mounted filesystem with ordered data mode. Opts: (null)
Dec 26 09:05:12 l05 kernel: [   31.189146] CIFS VFS: cifs_mount failed w/return code = -6
Dec 26 09:05:12 l05 kernel: [   31.190460] CIFS VFS: cifs_mount failed w/return code = -6

Dec 26 09:07:12 l05 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Dec 26 09:07:12 l05 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1293" x-info="http://www.rsyslog.com"] start
Dec 26 09:07:12 l05 rsyslogd: rsyslogd's groupid changed to 103
Dec 26 09:07:12 l05 rsyslogd: rsyslogd's userid changed to 101
Dec 26 09:07:12 l05 rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Dec 26 09:07:12 l05 kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 26 09:07:12 l05 kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 26 09:07:12 l05 kernel: [    0.000000] Linux version 3.2.0-57-generic (buildd@toyol) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 (Ubuntu 3.2.0-57.87-generic 3.2.52)
```

There are more in the zip file in attachments.

---

### Post by snooze101 on 2014-06-08
No fix,

Install Ubuntu 14.04  and seems to have so far resolved this issue.
All laptop functions keys, hardware (including dock) working Ubuntu 14.04 (was also working with Ubuntu 12.04).

Mark thread as solved.

---

