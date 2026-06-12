---
title: "unresponsiveness, working CPU"
date: 2007-06-12
forum: General Help
---

### Post by googlebytes on 2007-06-12
Please help! I first had this problem 2 weeks ago. I came back to the computer, and found the CPU running like crazy, and nothing would come up. This time it was Sat morn, Jun 9 – I kinda got the Firefox window up(it had been left up), but the CPU usage only let bits and pieces of mouse commands through. Two weeks ago I suspected spyware, but the only advice I got here was to check the system logs. I had turned off the computer though, and couldn't access the logs for that date by the time I got the advice.
The computer seemed to run normal afterward.

This time I let the computer keep running, because I wanted to bring up the system monitor and see what was using up all the CPU. By the afternoon, when I came back, my wife had got on the computer and all seemed normal, but I didn't have time to check it closely. Next day, Sunday, and the computer has restarted itself except I didn't have to enter a password. I did have to restart Firefox and Openoffice.  Now Firefox is running VERRRYYYY slowly. So what's goin on? Someone please help. I'm concerned Firefox has been compromised, or perhaps my whole system.

System monitor shows foomatic-rip and getty six times each. Also has a process called metacity (what's this?) that showed CPU usage even though it also showed it was sleeping. I am completely unfamiliar with all this.

The system logs contained the following (edited to improve brevity):

auth.log

Jun  9 00:17:01 owner-desktop CRON[6450]: (pam_unix) session opened for user root by (uid=0)
Jun  9 00:17:01 owner-desktop CRON[6450]: (pam_unix) session closed for user root
Jun  9 01:17:01 owner-desktop CRON[7902]: (pam_unix) session opened for user root by (uid=0)
Jun  9 01:17:01 owner-desktop CRON[7902]: (pam_unix) session closed for user root
Jun  9 02:17:01 owner-desktop CRON[9355]: (pam_unix) session opened for user root by (uid=0)
Jun  9 02:17:01 owner-desktop CRON[9355]: (pam_unix) session closed for user root
Jun  9 03:17:02 owner-desktop CRON[10811]: (pam_unix) session opened for user root by (uid=0)
Jun  9 03:17:02 owner-desktop CRON[10811]: (pam_unix) session closed for user root
Jun  9 04:17:03 owner-desktop CRON[12275]: (pam_unix) session opened for user root by (uid=0)
Jun  9 04:17:04 owner-desktop CRON[12275]: (pam_unix) session closed for user root
Jun  9 05:17:03 owner-desktop CRON[13733]: (pam_unix) session opened for user root by (uid=0)
Jun  9 05:17:04 owner-desktop CRON[13733]: (pam_unix) session closed for user root
Jun  9 06:17:05 owner-desktop CRON[15016]: (pam_unix) session opened for user root by (uid=0)
Jun  9 06:17:08 owner-desktop CRON[15016]: (pam_unix) session closed for user root
Jun  9 06:25:08 owner-desktop CRON[15175]: (pam_unix) session opened for user root by (uid=0)
Jun  9 06:25:12 owner-desktop CRON[15175]: (pam_unix) session closed for user root
Jun  9 07:17:05 owner-desktop CRON[16114]: (pam_unix) session opened for user root by (uid=0)
Jun  9 07:17:14 owner-desktop CRON[16114]: (pam_unix) session closed for user root
Jun  9 07:30:06 owner-desktop CRON[16345]: (pam_unix) session opened for user root by (uid=0)
Jun  9 07:30:54 owner-desktop CRON[16345]: (pam_unix) session closed for user root
Jun  9 08:18:17 owner-desktop CRON[16637]: (pam_unix) session opened for user root by (uid=0)
Jun  9 08:20:06 owner-desktop CRON[16637]: (pam_unix) session closed for user root
Jun  9 09:18:13 owner-desktop CRON[16680]: (pam_unix) session opened for user root by (uid=0)
Jun  9 09:18:58 owner-desktop CRON[16680]: (pam_unix) session closed for user root
Jun  9 10:17:57 owner-desktop CRON[16684]: (pam_unix) session opened for user root by (uid=0)
Jun  9 10:19:07 owner-desktop CRON[16684]: (pam_unix) session closed for user root
Jun  9 11:19:54 owner-desktop CRON[16695]: (pam_unix) session opened for user root by (uid=0)
Jun  9 11:21:36 owner-desktop CRON[16695]: (pam_unix) session closed for user root
Jun  9 12:17:01 owner-desktop CRON[16810]: (pam_unix) session opened for user root by (uid=0)
Jun  9 12:17:02 owner-desktop CRON[16810]: (pam_unix) session closed for user root
Jun  9 13:17:01 owner-desktop CRON[16825]: (pam_unix) session opened for user root by (uid=0)
Jun  9 13:17:01 owner-desktop CRON[16825]: (pam_unix) session closed for user root
Jun  9 14:17:01 owner-desktop CRON[16851]: (pam_unix) session opened for user root by (uid=0)
Jun  9 14:17:02 owner-desktop CRON[16851]: (pam_unix) session closed for user root
Jun  9 15:17:01 owner-desktop CRON[16866]: (pam_unix) session opened for user root by (uid=0)
Jun  9 15:17:01 owner-desktop CRON[16866]: (pam_unix) session closed for user root
Jun  9 16:17:01 owner-desktop CRON[16884]: (pam_unix) session opened for user root by (uid=0)
Jun  9 16:17:01 owner-desktop CRON[16884]: (pam_unix) session closed for user root
Jun  9 17:17:02 owner-desktop CRON[16898]: (pam_unix) session opened for user root by (uid=0)
Jun  9 17:17:02 owner-desktop CRON[16898]: (pam_unix) session closed for user root
Jun  9 18:17:01 owner-desktop CRON[16919]: (pam_unix) session opened for user root by (uid=0)
Jun  9 18:17:02 owner-desktop CRON[16919]: (pam_unix) session closed for user root
Jun  9 19:17:01 owner-desktop CRON[16935]: (pam_unix) session opened for user root by (uid=0)
Jun  9 19:17:02 owner-desktop CRON[16935]: (pam_unix) session closed for user root
Jun  9 20:17:01 owner-desktop CRON[16944]: (pam_unix) session opened for user root by (uid=0)
Jun  9 20:17:01 owner-desktop CRON[16944]: (pam_unix) session closed for user root
Jun  9 21:17:01 owner-desktop CRON[16960]: (pam_unix) session opened for user root by (uid=0)
Jun  9 21:17:02 owner-desktop CRON[16960]: (pam_unix) session closed for user root
Jun  9 22:17:02 owner-desktop CRON[16976]: (pam_unix) session opened for user root by (uid=0)
Jun  9 22:17:02 owner-desktop CRON[16976]: (pam_unix) session closed for user root
Jun  9 23:17:01 owner-desktop CRON[16991]: (pam_unix) session opened for user root by (uid=0)
Jun  9 23:17:01 owner-desktop CRON[16991]: (pam_unix) session closed for user root

Daemon.log
Jun  8 05:54:03 owner-desktop dhclient: DHCPACK from 10.0.0.2
Jun  8 05:54:04 owner-desktop dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Jun  8 05:54:04 owner-desktop dhclient: bound to 10.0.0.11 -- renewal in 37721 seconds.
Jun  8 16:22:45 owner-desktop dhclient: DHCPREQUEST on eth0 to 10.0.0.2 port 67
Jun  8 16:22:45 owner-desktop dhclient: DHCPACK from 10.0.0.2
Jun  8 16:22:46 owner-desktop dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Jun  8 16:22:46 owner-desktop dhclient: bound to 10.0.0.11 -- renewal in 40308 seconds.
Jun  9 03:34:36 owner-desktop dhclient: DHCPREQUEST on eth0 to 10.0.0.2 port 67
Jun  9 03:34:36 owner-desktop dhclient: DHCPACK from 10.0.0.2
Jun  9 03:34:38 owner-desktop dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Jun  9 03:34:38 owner-desktop dhclient: bound to 10.0.0.11 -- renewal in 35794 seconds.
Jun  9 13:31:14 owner-desktop dhclient: DHCPREQUEST on eth0 to 10.0.0.2 port 67
Jun  9 13:31:14 owner-desktop dhclient: DHCPACK from 10.0.0.2
Jun  9 13:31:15 owner-desktop dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Jun  9 13:31:15 owner-desktop dhclient: bound to 10.0.0.11 -- renewal in 40061 seconds.
Jun 10 00:38:59 owner-desktop dhclient: DHCPREQUEST on eth0 to 10.0.0.2 port 67
Jun 10 00:38:59 owner-desktop dhclient: DHCPACK from 10.0.0.2
Jun 10 00:39:01 owner-desktop dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Jun 10 00:39:01 owner-desktop dhclient: bound to 10.0.0.11 -- renewal in 41083 seconds.
Jun 10 12:03:44 owner-desktop dhclient: DHCPREQUEST on eth0 to 10.0.0.2 port 67
Jun 10 12:03:45 owner-desktop dhclient: DHCPACK from 10.0.0.2
Jun 10 12:03:45 owner-desktop dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Jun 10 12:03:45 owner-desktop dhclient: bound to 10.0.0.11 -- renewal in 40984 seconds.

messages

Jun  8 21:48:08 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  8 21:48:38 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  8 21:48:49 owner-desktop kernel: [17730208.392000] Inbound IN=eth0 OUT= MAC=00:04:5a:40:eb:af:00:40:36:19:aa:00:08:00 SRC=216.252.99.234 DST=10.0.0.11 LEN=190 TOS=0x00 PREC=0x00 TTL=53 ID=2896 DF PROTO=TCP SPT=80 DPT=46555 WINDOW=64108 RES=0x00 ACK PSH URGP=0 
Jun  8 21:49:08 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  8 21:49:38 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  8 21:50:38 owner-desktop last message repeated 2 times
Jun  8 21:51:38 owner-desktop last message repeated 2 times
.
.
.

Jun  8 23:59:53 owner-desktop last message repeated 2 times
Jun  9 00:00:53 owner-desktop last message repeated 2 times
Jun  9 00:01:53 owner-desktop last message repeated 2 times
.
.
.

Jun  9 05:42:18 owner-desktop last message repeated 2 times
Jun  9 05:42:48 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 05:43:50 owner-desktop last message repeated 2 times
.
.
.

Jun  9 06:12:33 owner-desktop last message repeated 2 times
Jun  9 06:13:09 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 06:14:11 owner-desktop last message repeated 2 times
.
.
.

Jun  9 06:46:06 owner-desktop last message repeated 2 times
Jun  9 06:46:36 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 06:47:40 owner-desktop last message repeated 2 times
.
.
.

Jun  9 07:13:30 owner-desktop last message repeated 2 times
Jun  9 07:14:00 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 07:15:32 owner-desktop last message repeated 3 times
Jun  9 07:16:33 owner-desktop last message repeated 2 times
Jun  9 07:17:04 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 07:18:07 owner-desktop last message repeated 2 times
.
.
.

Jun  9 07:34:46 owner-desktop last message repeated 2 times
Jun  9 07:35:21 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 07:36:25 owner-desktop last message repeated 2 times
.
.
.
{at this point I'm trying to get on the computer}
Jun  9 07:44:59 owner-desktop last message repeated 2 times
Jun  9 07:45:30 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 07:46:45 owner-desktop last message repeated 2 times
Jun  9 07:48:11 owner-desktop last message repeated 2 times
Jun  9 07:49:04 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 07:49:34 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 07:51:03 owner-desktop last message repeated 2 times
Jun  9 07:51:36 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 07:53:36 owner-desktop last message repeated 3 times
Jun  9 07:54:11 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 07:55:24 owner-desktop last message repeated 2 times
Jun  9 07:56:25 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 07:57:32 owner-desktop last message repeated 2 times
Jun  9 07:58:47 owner-desktop last message repeated 2 times
Jun  9 07:59:47 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:00:47 owner-desktop last message repeated 2 times
Jun  9 08:02:03 owner-desktop last message repeated 2 times
Jun  9 08:03:10 owner-desktop last message repeated 2 times
Jun  9 08:03:50 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:05:05 owner-desktop last message repeated 2 times
Jun  9 08:06:34 owner-desktop last message repeated 2 times
Jun  9 08:07:23 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:07:56 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:09:36 owner-desktop last message repeated 2 times
Jun  9 08:10:46 owner-desktop last message repeated 2 times
Jun  9 08:11:55 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:12:33 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:14:12 owner-desktop last message repeated 2 times
Jun  9 08:15:05 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:16:13 owner-desktop last message repeated 2 times
Jun  9 08:17:15 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:17:52 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:19:35 owner-desktop last message repeated 2 times
Jun  9 08:20:40 owner-desktop last message repeated 2 times
Jun  9 08:21:12 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:22:35 owner-desktop last message repeated 2 times
Jun  9 08:24:07 owner-desktop last message repeated 2 times
Jun  9 08:24:42 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:26:16 owner-desktop last message repeated 2 times
Jun  9 08:27:09 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:28:17 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:28:56 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:30:04 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:31:49 owner-desktop last message repeated 2 times
Jun  9 08:32:43 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:34:04 owner-desktop last message repeated 2 times
Jun  9 08:35:16 owner-desktop last message repeated 2 times
Jun  9 08:36:24 owner-desktop last message repeated 2 times
Jun  9 08:37:13 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:38:23 owner-desktop last message repeated 2 times
Jun  9 08:39:28 owner-desktop last message repeated 2 times
Jun  9 08:40:25 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:41:38 owner-desktop last message repeated 2 times
Jun  9 08:42:42 owner-desktop last message repeated 2 times
Jun  9 08:43:23 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:45:02 owner-desktop last message repeated 3 times
Jun  9 08:45:38 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:46:50 owner-desktop last message repeated 2 times
Jun  9 08:48:06 owner-desktop last message repeated 2 times
Jun  9 08:48:50 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:49:58 owner-desktop last message repeated 2 times
Jun  9 08:51:07 owner-desktop last message repeated 2 times
Jun  9 08:52:30 owner-desktop last message repeated 2 times
Jun  9 08:53:15 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:54:36 owner-desktop last message repeated 2 times
Jun  9 08:55:09 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 08:56:30 owner-desktop last message repeated 2 times
Jun  9 08:57:52 owner-desktop last message repeated 2 times
Jun  9 08:58:32 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:00:00 owner-desktop last message repeated 2 times
Jun  9 09:01:04 owner-desktop last message repeated 2 times
Jun  9 09:01:47 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:02:57 owner-desktop last message repeated 2 times
Jun  9 09:04:01 owner-desktop last message repeated 2 times
Jun  9 09:05:31 owner-desktop last message repeated 2 times
Jun  9 09:06:11 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:07:52 owner-desktop last message repeated 2 times
Jun  9 09:08:22 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:09:52 owner-desktop last message repeated 2 times
Jun  9 09:10:31 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:12:00 owner-desktop last message repeated 2 times
Jun  9 09:12:52 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:13:58 owner-desktop last message repeated 2 times
Jun  9 09:15:11 owner-desktop last message repeated 2 times
Jun  9 09:16:23 owner-desktop last message repeated 2 times
Jun  9 09:17:45 owner-desktop last message repeated 2 times
Jun  9 09:18:41 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:19:18 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:20:47 owner-desktop last message repeated 2 times
Jun  9 09:21:42 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:23:01 owner-desktop last message repeated 2 times
Jun  9 09:23:39 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:25:13 owner-desktop last message repeated 2 times
Jun  9 09:26:33 owner-desktop last message repeated 2 times
Jun  9 09:27:53 owner-desktop last message repeated 2 times
Jun  9 09:29:10 owner-desktop last message repeated 2 times
Jun  9 09:30:20 owner-desktop last message repeated 2 times
Jun  9 09:31:21 owner-desktop last message repeated 2 times
Jun  9 09:32:10 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:33:20 owner-desktop last message repeated 2 times
Jun  9 09:34:13 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:35:26 owner-desktop last message repeated 2 times
Jun  9 09:36:40 owner-desktop last message repeated 2 times
Jun  9 09:37:45 owner-desktop last message repeated 2 times
Jun  9 09:38:57 owner-desktop last message repeated 2 times
Jun  9 09:40:25 owner-desktop last message repeated 2 times
Jun  9 09:41:12 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:42:44 owner-desktop last message repeated 2 times
Jun  9 09:43:37 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:44:55 owner-desktop last message repeated 2 times
Jun  9 09:45:40 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:47:04 owner-desktop last message repeated 2 times
Jun  9 09:47:54 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:48:45 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:50:18 owner-desktop last message repeated 2 times
Jun  9 09:51:10 owner-desktop last message repeated 2 times
Jun  9 09:52:27 owner-desktop last message repeated 2 times
Jun  9 09:53:41 owner-desktop last message repeated 2 times
Jun  9 09:54:27 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:55:35 owner-desktop last message repeated 2 times
Jun  9 09:56:55 owner-desktop last message repeated 2 times
Jun  9 09:57:57 owner-desktop last message repeated 2 times
Jun  9 09:58:36 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 09:59:57 owner-desktop last message repeated 2 times
Jun  9 10:01:10 owner-desktop last message repeated 2 times
Jun  9 10:02:26 owner-desktop last message repeated 2 times
Jun  9 10:03:33 owner-desktop last message repeated 2 times
Jun  9 10:04:41 owner-desktop last message repeated 2 times
Jun  9 10:05:20 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:06:34 owner-desktop last message repeated 2 times
Jun  9 10:07:58 owner-desktop last message repeated 2 times
Jun  9 10:09:00 owner-desktop last message repeated 2 times
Jun  9 10:09:52 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:11:09 owner-desktop last message repeated 2 times
Jun  9 10:12:06 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:13:21 owner-desktop last message repeated 2 times
Jun  9 10:14:21 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:15:47 owner-desktop last message repeated 2 times
Jun  9 10:16:57 owner-desktop last message repeated 2 times
Jun  9 10:17:47 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:18:55 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:20:25 owner-desktop last message repeated 2 times
Jun  9 10:21:51 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:23:00 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:23:42 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:24:22 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:26:16 owner-desktop last message repeated 2 times
Jun  9 10:26:56 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:28:31 owner-desktop last message repeated 2 times
Jun  9 10:30:02 owner-desktop last message repeated 2 times
Jun  9 10:30:48 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:32:17 owner-desktop last message repeated 2 times
Jun  9 10:32:58 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:34:12 owner-desktop last message repeated 2 times
Jun  9 10:36:10 owner-desktop last message repeated 2 times
Jun  9 10:37:26 owner-desktop last message repeated 2 times
Jun  9 10:38:03 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:39:16 owner-desktop last message repeated 2 times
Jun  9 10:40:31 owner-desktop last message repeated 2 times
Jun  9 10:41:09 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:42:32 owner-desktop last message repeated 2 times
Jun  9 10:43:45 owner-desktop last message repeated 2 times
Jun  9 10:45:10 owner-desktop last message repeated 2 times
Jun  9 10:46:06 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:47:29 owner-desktop last message repeated 2 times
Jun  9 10:48:17 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:48:56 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:50:18 owner-desktop last message repeated 2 times
Jun  9 10:52:03 owner-desktop last message repeated 2 times
Jun  9 10:53:02 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:54:08 owner-desktop last message repeated 2 times
Jun  9 10:55:02 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:56:08 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:57:05 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 10:58:57 owner-desktop last message repeated 2 times
Jun  9 10:59:46 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:00:43 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:02:27 owner-desktop last message repeated 2 times
Jun  9 11:03:34 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:04:54 owner-desktop last message repeated 2 times
Jun  9 11:05:51 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:06:44 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:07:53 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:09:10 owner-desktop last message repeated 2 times
Jun  9 11:09:48 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:11:12 owner-desktop last message repeated 2 times
Jun  9 11:12:36 owner-desktop last message repeated 2 times
Jun  9 11:13:35 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:14:30 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:15:20 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:16:17 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:17:34 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:19:29 owner-desktop last message repeated 2 times
Jun  9 11:21:02 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:22:19 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:23:07 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:23:56 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:25:02 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:26:04 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:27:10 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:29:26 owner-desktop last message repeated 2 times
Jun  9 11:31:01 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:32:34 owner-desktop kernel: [17779623.428000] oom-killer: gfp_mask=0x201d2, order=0
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000]  <c014f6e2> out_of_memory+0x132/0x160  <c0151656> __alloc_pages+0x306/0x330
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000]  <c0152c91> __do_page_cache_readahead+0x111/0x270  <c02d9a86> io_schedule+0x26/0x30
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000]  <c02da19b> __wait_on_bit_lock+0x5b/0x70  <c014bae0> sync_page+0x0/0x40
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000]  <c014bad5> __lock_page+0x75/0x80  <c014ebc5> filemap_nopage+0x2c5/0x3a0
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000]  <c012bd4a> run_timer_softirq+0x3a/0x1a0  <c0158e62> __handle_mm_fault+0x132/0x900
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000]  <c02dbf30> do_page_fault+0x0/0x6f0  <c010408a> common_interrupt+0x1a/0x20
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000]  <c02dc30b> do_page_fault+0x3db/0x6f0  <c02dbf30> do_page_fault+0x0/0x6f0
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000]  <c010420f> error_code+0x4f/0x60 
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000] Mem-info:
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000] DMA per-cpu:
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000] cpu 0 hot: high 0, batch 1 used:0
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000] cpu 0 cold: high 0, batch 1 used:0
Jun  9 11:32:37 owner-desktop kernel: [17779623.428000] DMA32 per-cpu: empty
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] Normal per-cpu:
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] cpu 0 hot: high 90, batch 15 used:50
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] cpu 0 cold: high 30, batch 7 used:6
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] HighMem per-cpu: empty
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] Free pages:        3492kB (0kB HighMem)
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] Active:51048 inactive:21124 dirty:0 writeback:0 unstable:0 free:873 slab:2615 mapped:71266 pagetables:762
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] DMA free:1324kB min:112kB low:140kB high:168kB active:5784kB inactive:4632kB present:16384kB pages_scanned:10713 all_unreclaimable? yes
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] lowmem_reserve[]: 0 0 303 303
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] DMA32 free:0kB min:0kB low:0kB high:0kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] lowmem_reserve[]: 0 0 303 303
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] Normal free:2168kB min:2168kB low:2708kB high:3252kB active:198408kB inactive:79864kB present:310272kB pages_scanned:68980 all_unreclaimable? no
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] lowmem_reserve[]: 0 0 0 0
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] HighMem free:0kB min:128kB low:128kB high:128kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] lowmem_reserve[]: 0 0 0 0
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] DMA: 1*4kB 1*8kB 0*16kB 1*32kB 0*64kB 0*128kB 1*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1324kB
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] DMA32: empty
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] Normal: 18*4kB 0*8kB 1*16kB 1*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 2168kB
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] HighMem: empty
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] Swap cache: add 491589, delete 491589, find 70042/102914, race 0+0
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] Free swap  = 0kB
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] Total swap = 931728kB
Jun  9 11:32:40 owner-desktop kernel: [17779623.428000] Free swap:            0kB
Jun  9 11:32:40 owner-desktop kernel: [17779623.444000] 81664 pages of RAM
Jun  9 11:32:40 owner-desktop kernel: [17779623.444000] 0 pages of HIGHMEM
Jun  9 11:32:40 owner-desktop kernel: [17779623.444000] 1720 reserved pages
Jun  9 11:32:40 owner-desktop kernel: [17779623.444000] 2678 pages shared
Jun  9 11:32:40 owner-desktop kernel: [17779623.444000] 0 pages swap cached
Jun  9 11:32:40 owner-desktop kernel: [17779623.444000] 0 pages dirty
Jun  9 11:32:40 owner-desktop kernel: [17779623.444000] 0 pages writeback
Jun  9 11:32:40 owner-desktop kernel: [17779623.444000] 71266 pages mapped
Jun  9 11:32:40 owner-desktop kernel: [17779623.444000] 2615 pages slab
Jun  9 11:32:40 owner-desktop kernel: [17779623.444000] 762 pages pagetables
Jun  9 11:32:57 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:33:11 owner-desktop no_device_found: invalid ModelQueryResult: msg=modelqueryresult result-code=48  prnt/hpijs/hplip_api.c 396 
Jun  9 11:33:11 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:33:57 owner-desktop last message repeated 3 times
Jun  9 11:34:57 owner-desktop last message repeated 4 times
Jun  9 11:35:58 owner-desktop last message repeated 4 times
Jun  9 11:36:58 owner-desktop last message repeated 4 times
Jun  9 11:37:58 owner-desktop last message repeated 4 times
Jun  9 11:38:58 owner-desktop last message repeated 4 times
Jun  9 11:39:58 owner-desktop last message repeated 4 times
Jun  9 11:40:59 owner-desktop last message repeated 4 times
Jun  9 11:41:59 owner-desktop last message repeated 4 times
Jun  9 11:42:59 owner-desktop last message repeated 4 times
Jun  9 11:43:43 owner-desktop last message repeated 3 times
Jun  9 11:43:47 owner-desktop exiting on signal 15
Jun  9 11:43:49 owner-desktop syslogd 1.4.1#18ubuntu6: restart.
Jun  9 11:43:59 owner-desktop no_device_found: INFO: open device failed; will retry in 30 seconds... 
Jun  9 11:44:43 owner-desktop last message repeated 3 times
Jun  9 11:45:43 owner-desktop last message repeated 4 times
.
.
.

Jun  9 12:00:47 owner-desktop last message repeated 4 times

 };
(EE) Error loading keymap /var/lib/xkb/server-0.xkm

---

### Post by googlebytes on 2007-06-12
logs cont

syslog(no Jun 9 available)
Jun 10
Jun 10 08:34:46 owner-desktop syslogd 1.4.1#18ubuntu6: restart.

Xorg.0.log

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux owner-desktop 2.6.17-11-generic #2 SMP Tue Mar 13 23:32:38 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun  2 12:51:48 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "EN9410"
(**) |   |-->Device "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7124 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7125 card 0e11,b165 rev 03 class 03,00,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2418 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2410 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2411 card 8086,2411 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2412 card 8086,2412 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2413 card 8086,2413 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:05:0: chip 125d,1988 card 0e11,b19d rev 12 class 04,01,00 hdr 00
(II) PCI: 01:0a:0: chip 1317,0985 card 1317,0570 rev 11 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[2] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[3] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x40000000 - 0x400fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x200fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:1:0) Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] rev 3, Mem @ 0x44000000/26, 0x40100000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[1] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[2] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[3] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[4] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[5] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[6] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[7] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[1] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[2] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[3] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[4] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[5] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[6] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[7] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[5] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[6] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[9] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[10] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[11] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[12] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[13] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.6.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:01:0
(--) Chipset i810e found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[5] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[6] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[9] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[10] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[11] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[12] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[13] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[5] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[6] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[7] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[8] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[9] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[14] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[15] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[16] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[17] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[18] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(**) I810(0): Depth 24, (--) framebuffer bpp 24
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(**) I810(0): DRI is disabled because it runs only at 16-bit depth.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 2.0
(II) I810(0): VESA VBE Total Mem: 1024 kB
(II) I810(0): VESA VBE OEM: Intel810(TM) Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 32.18
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: i810 Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level none
(II) I810(0): VESA VBE DDC transfer in appr. 0 sec.
(II) I810(0): VESA VBE DDC read failed
(--) I810(0): Chipset: "i810e"
(--) I810(0): Linear framebuffer at 0x44000000
(--) I810(0): IO registers at addr 0x40100000
(II) I810(0): Kernel reported 67072 total, 1 used
(II) I810(0): I810CheckAvailableMemory: 268284k available
(==) I810(0): Will alloc AGP framebuffer: 8192 kByte
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): EN9410: Using default hsync range of 31.50-37.90 kHz
(II) I810(0): EN9410: Using default vrefresh range of 50.00-70.00 Hz
(II) I810(0): Clock range:   9.50 to 136.00 MHz
(II) I810(0): Not using default mode "640x350" (vrefresh out of range)
(II) I810(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x400" (vrefresh out of range)
(II) I810(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "720x400" (vrefresh out of range)
(II) I810(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (vrefresh out of range)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (vrefresh out of range)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (hsync out of range)
(II) I810(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (hsync out of range)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (hsync out of range)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (hsync out of range)
(II) I810(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (unknown reason)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (hsync out of range)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (hsync out of range)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (hsync out of range)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1024x768" (hsync out of range)
(II) I810(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1152x864" (hsync out of range)
(II) I810(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x960" (hsync out of range)
(II) I810(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x1024" (hsync out of range)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x1024" (hsync out of range)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "832x624" (hsync out of range)
(II) I810(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x768" (hsync out of range)
(II) I810(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1280x800" (hsync out of range)
(II) I810(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1152x768" (hsync out of range)
(II) I810(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1152x864" (hsync out of range)
(II) I810(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (hsync out of range)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1440x900" (hsync out of range)
(II) I810(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1600x1024" (hsync out of range)
(II) I810(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) I810(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) I810(0): Not using mode "1280x1024" (no mode of this name)
(II) I810(0): Not using mode "1152x864" (no mode of this name)
(II) I810(0): Not using mode "1024x768" (no mode of this name)
(II) I810(0): Not using mode "832x624" (no mode of this name)
(II) I810(0): Not using mode "720x400" (no mode of this name)
(--) I810(0): Virtual size is 800x600 (pitch 1024)
(**) I810(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) I810(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) I810(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) I810(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) I810(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) I810(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(==) I810(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) I810(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x40100000 - 0x4017ffff (0x80000) MS[B]
	[1] 0	0	0x44000000 - 0x47ffffff (0x4000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[7] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[8] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[15] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[16] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[17] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[18] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[19] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[20] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) I810(0): Write-combining range (0x44000000,0x4000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) I810(0): Setting dot clock to 40.0 MHz [ 0x8 0x1 0x30 ] [ 10 3 3 ]
(II) I810(0): chose watermark 0x2210c000: (tab.freq 40.0)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x00000000 (pgoffset 0)
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1024 pages failed
	(Cannot allocate memory)
(II) I810(0): No physical memory available for 4194304 bytes of DCACHE
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x00800000 (pgoffset 2048)
(II) I810(0): Allocated of 4096 bytes for HW cursor
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x00801000 (pgoffset 2049)
(II) I810(0): Allocated of 16384 bytes for ARGB HW cursor
(II) I810(0): Adding 512 scanlines for pixmap caching
(II) I810(0): Allocated Scratch Memory
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		20 128x128 slots
		4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(**) Option "dpms"
(**) I810(0): DPMS enabled
(WW) I810(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
    xkb_types                { include "%" };
    xkb_compatibility        { include "%" };
    xkb_symbols              { include "%" };
    xkb_geometry             { include "%" };
(EE) Error loading keymap /var/lib/xkb/server-0.xkm
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
    xkb_types                { include "%" };
    xkb_compatibility        { include "%" };
    xkb_symbols              { include "%" };
    xkb_geometry             { include "%"

---

### Post by tgalati4 on 2007-06-12
In a terminal:

sudo apt-get install htop
htop  (control-C to quit or use the mouse and click on quit)

What process is using the most CPU time?

Your system logs show a problem with hplip trying to open a device that doesn't exist.  Did you set up a printer and that printer is no longer connected?  If so, then reconnect the printer or delete the printer.  I sometimes get a lot of CPU activity if I disconnect a parallel port printer and don't reconnect it.

There is usually no need to post the entire log file, just a snippet of recurring messages will do.

---

### Post by googlebytes on 2007-06-12
Thank you for your reply. - yes, the system did not have an installation choice for my brother printer, so I chose Brother 8300to see if it would work - it didn't.  Just now when I went under System>Administration>Printing it showed the 8300 trying to print 2 documents, so I deleted the printer. Firefox is still vERRRy slow.

The computer is not disabled now like it was with extreme CPU usage. Currently most of the Cpu usage is from the Firefox bin(about 40%), gnome-cups-icon (about 40%), gnome-system-monitor (about 10%), and Xorg(around 8%). Sat the light was flashing, and you could hear it grinding away, so I guess the hard drive was working too.

---

### Post by googlebytes on 2007-06-12
should I kill some of the six "getty"s or "foomatic-rip"s running?

---

### Post by googlebytes on 2007-06-12
Well, they are "sleeping" right now.

---

### Post by tgalati4 on 2007-06-12
gnome-cups-icon is known to have problems with printers that are not working or not powered on, so I would kill that process first.  Be sure to delete the printer from CUPS as well, because that will continue to cause problems.  Then restart cups:

sudo /etc/init.d/cupsys restart

Good luck.

---

### Post by googlebytes on 2007-06-13
Thank you again - I am on my way to being mended.
When I restarted Firefox, things have been back to normal.
Do I have to reboot to use htop? So far it doesn't seem to do anything.
How do I delete a printer in cups?

---

