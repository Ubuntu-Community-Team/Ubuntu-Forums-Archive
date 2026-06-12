---
title: "NTP sync time with 30 minutes ago"
date: 2017-10-30
forum: General Help
---

### Post by EarthCrash on 2017-10-30
I've got 35 new ubuntu 14.04 server(dedicated, not VM) in company and trying to sync my company's internal NTP server isn't successful.
Before install ntp & sync with internal ntp server, servers' time is different about 10~50 minute ago/far.(at least i think)
After install and configuration for company's internal ntp in 25 servers, almost of them(about 20 of 25) sync time with exactly 30 minutes ago.(they sync with ntp server anyway, though)

So i do test when 10 servers left for installing ntp. Sync time manually by 'date' command and install ntp.(including confuguration)
And then, all of them work perfectly.

Then i've take serveral action for resolve this situation and all of them failed.
(1) stop ntp, manually sync time by date command, start ntp
(2) ntpd command with -q, -g,  or whatever.
(3) reinstall ntp(without, then with purge)

All of them(35) have same configuration but still can't sync time properly if don't sync time before first ntp install.
Maybe this isn't problem about internal ntp server because company's thousands servers ntp works fine with them.

What i missing in this?

---

### Post by TheFu on 2017-10-31
I dind't think that ntp would sync if time was too far off. A daily rdate might be just what you need to get them "close."

I have seen issues on my 14.04 NTP server machine where Windows clients wouldn't sync anymore. Windows thinks that +/- 5min is close enough, BTW.  My TV recording machine (Win7) hasn't been able to sync with my 14.04 server the last few weeks.  There wasn't any issue the previous ... er ... 7 yrs.  That 14.04 NTP server was 10.04 prior to the move to 14.04.

If you can post your ntp.conf that is used on each client machine, someone might see issues.  Please remove all the comments.  I have only 1 NTP server specified in the ntp.conf and it has an IP, not hostname/dns.  I use ansible to push out config changes to all our machines here.

But you probably know more about this than I do.

---

