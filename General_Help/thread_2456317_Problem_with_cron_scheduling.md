---
title: "Problem with cron scheduling"
date: 2021-01-09
forum: General Help
---

### Post by hajdui on 2021-01-09
Hello,

I just installed ubuntu server to a raspberrypi. Earlier I used raspbian buster and did not experience the below problem.
I set up some jobs to root crontab.

Mount on starup works:
@reboot mount /dev/sda /media/pi

Wakeonlan scheduled to a date doesn't work (every day at 06:30):
30 06 * * * /usr/sbin/etherwake 70:85:C2:72:4F:F80
Otherwise the command itself works.

For testing purpose I set up these:
* * * * * echo ‘Run this command every minute’ >> /media/pi/every_min.txt
32 12 * * * echo ‘Run this command at a specific timely’ >> /media/pi/spec_time.txt
The first one works (create an entry evry minute) but the second one never.

sudo grep CRON /var/log/syslog
this command shows the successfull jobs but nothing about the failed.

Could you please help me what might have gone wrong?

---

### Post by spjackson on 2021-01-09
The format of the examples you have given look fine. Here are 2 thoughts.

[LIST=1]
[*]Perhaps you are editing the file directly rather than via 'crontab -e', in which case cron would not receive a signal to re-read the file.
[*]Perhaps your system default timezone isn't what you expect.
[/LIST]
 
Maybe it's something else, but those are my 2 thoughts.

---

### Post by hajdui on 2021-01-10
Hello,

The default time zone had to be corrected.
Thanks for the help!

---

