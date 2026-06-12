---
title: "Dapper is rebooting a lot on my old machines"
date: 2006-11-25
forum: General Help
---

### Post by whateverdood on 2006-11-25
I installed Dapper a month or two ago (using the alternate CD) on an old AMD K6-2 machine and I've noticed the machine reboots itself *a lot*.  I'm using the box as a head-less host for some research/analysis and this is getting in the way...

Does anyone have any ideas?  Is there anything I can do to fix this?  Thanks in advance!

Here's a snippet from 'last':

-snip-
[FONT="courier new"]dood@baloo:~$ last
dood     pts/0        192.168.1.102    Sat Nov 25 06:36   still logged in
reboot   system boot  2.6.15-26-386    Sat Nov 25 03:56          (02:39)
reboot   system boot  2.6.15-26-386    Fri Nov 24 11:45          (18:50)
reboot   system boot  2.6.15-26-386    Fri Nov 24 08:33          (22:02)
dood     pts/0        192.168.1.102    Thu Nov 23 07:35 - 07:37  (00:01)
reboot   system boot  2.6.15-26-386    Thu Nov 23 06:43         (1+23:53)
dood     pts/0        192.168.1.102    Wed Nov 22 19:36 - 19:36  (00:00)
dood     pts/0        192.168.1.102    Wed Nov 22 18:58 - 19:20  (00:21)
dood     pts/0        192.168.1.102    Wed Nov 22 15:53 - 16:21  (00:27)
dood     pts/0        192.168.1.102    Wed Nov 22 07:25 - 07:31  (00:05)
dood     pts/0        192.168.1.100    Tue Nov 21 19:28 - 21:41  (02:13)
dood     pts/0        192.168.1.100    Tue Nov 21 18:48 - 19:17  (00:28)
reboot   system boot  2.6.15-26-386    Tue Nov 21 08:27         (3+22:08)
reboot   system boot  2.6.15-26-386    Tue Nov 21 03:15         (4+03:20)
reboot   system boot  2.6.15-26-386    Tue Nov 21 00:44         (4+05:51)
dood     pts/0        192.168.1.101    Mon Nov 20 06:33 - 06:38  (00:04)
dood     pts/0        192.168.1.102    Sun Nov 19 14:45 - 15:43  (00:58)
[/FONT]-snip-

---

### Post by JeremyA on 2006-12-03
Is anything being logged in /var/log/messages around the times of the reboots?

---

### Post by whateverdood on 2006-12-05
This is the only thing I find near the reboot times:

[FONT="Courier New"]Dec  3 06:23:24 baloo -- MARK --
Dec  3 06:25:52 baloo exiting on signal 15
Dec  3 06:25:53 baloo syslogd 1.4.1#17ubuntu7: restart.
Dec  3 06:45:53 baloo -- MARK --[/FONT]

---

