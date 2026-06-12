---
title: "Configuring cron scripts"
date: 2007-11-23
forum: General Help
---

### Post by twill30 on 2007-11-23
I've just set up and configured a remote server running 6.06 LTS and now am establishing a daily/weekly workflow to stay on top of security checks etc.

I haven't used Ubuntu before so would appreciate some advice on running cron scripts.

The things I would like to have emailed to me daily are:

Log watch report
Tripwire report
RKHunter report

Nothing else.

At the moment, after a default install, I have (excuse long list):

cron.daily:

.placeholder
00logwatch
apt
apt-clean
aptitude
bsdmainutils
chrootkit
dlocate
exim
find
logcheck
logrotate
man-db
modutils
netkit-inetd
ntp-server
rkhunter
standard
syshlogd
tripwire

cron.weekly:

man-db
ntp-server
rkhunter
syshlogd

cron.monthly:

standard

Could someone please explain the steps to take in removing what I don't want/need (without breaking anything) and configuring what I do. I only want standard reports from the aforementioned 3 packages and don't want other log files getting clogged up etc...

---

