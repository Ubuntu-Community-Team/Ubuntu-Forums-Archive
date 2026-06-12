---
title: "enable banner at log in U 16.04?"
date: 2016-11-27
forum: General Help
---

### Post by kcragin on 2016-11-27
I am a newbie workingwith Ubuntu 16.04 and trying to get a banner to show after you log in, but Ican&#8217;t get it to show up- have tried making the banner in etc/issue.net,ect/motd and in sshd_config: set Print Motd yes and Banner /etc/issue.net, Banner/etc/ssh/sshd-banner, no default banner path, Banner /etc/motd. Then use sudo/etc/init.d/ssh restart and I just get the command line no banner. I am sure itis something simple, but I just don&#8217;t know where to go next. Have looked at alot of old posts pre-2008. Thanks for any help!

---

### Post by ian-weisser on 2016-11-27
Look at the manpage for the 'update-motd' command (man update-motd)
Look also at the /etc/update-motd.d/ directory for jobs that update motd.

---

