---
title: "Spamassassin, daily error - sa-update failed for unknown reasons"
date: 2014-07-09
forum: General Help
---

### Post by jimwillsher on 2014-07-09
Hello

Ubuntu 14.04 LTS.

For the last couple of weeks I've received a daily email:

/etc/cron.daily/spamassassin:
channel: could not find working mirror, channel failed sa-update failed for unknown reasons


If I run /etc/cron.daily/spamassassin manually it succeeds. if I run it via the cron job (copy the /etc/cron.daily/spamassassin to a new folder */tmp/x/* and then run *run-parts --report /tmp/x/*) it fails:


```
Jul  9 11:26:00.311 [20148] dbg: channel: file /var/lib/spamassassin/3.004000/updates_spamassassin_org/MIRRORED.BY is too old, refreshing mirrors file
Jul  9 11:26:00.311 [20148] dbg: channel: DNS lookup on mirrors.updates.spamassassin.org
Jul  9 11:26:00.503 [20148] dbg: http: url: [http://spamassassin.apache.org/updates/MIRRORED.BY](http://spamassassin.apache.org/updates/MIRRORED.BY)
Jul  9 11:26:00.503 [20148] dbg: http: downloading to: /var/lib/spamassassin/3.004000/updates_spamassassin_org/MIRRORED.BY, replace
Jul  9 11:26:00.503 [20148] dbg: util: executable for curl was found at /usr/bin/curl
Jul  9 11:26:00.503 [20148] dbg: http: /usr/bin/curl -s -L -O --remote-time -g --max-redirs 2 --connect-timeout 30 --max-time 300 --fail -o MIRRORED.BY -- [http://spamassassin.apache.org/updates/MIRRORED.BY](http://spamassassin.apache.org/updates/MIRRORED.BY)
Jul  9 11:26:00.730 [20148] dbg: http: process [20149], exit status: 5888
Jul  9 11:26:00.730 [20148] dbg: channel: no mirror data available for channel updates.spamassassin.org from [http://spamassassin.apache.org/updates/MIRRORED.BY](http://spamassassin.apache.org/updates/MIRRORED.BY)
error: unable to refresh mirrors file for channel updates.spamassassin.org, using old file
Jul  9 11:26:00.730 [20148] dbg: channel: reading MIRRORED.BY file /var/lib/spamassassin/3.004000/updates_spamassassin_org/MIRRORED.BY
Jul  9 11:26:00.730 [20148] dbg: channel: parsing MIRRORED.BY file for channel updates.spamassassin.org
Jul  9 11:26:00.731 [20148] dbg: channel: found mirror [http://sa-update.dnswl.org/](http://sa-update.dnswl.org/) weight=1
Jul  9 11:26:00.731 [20148] dbg: channel: found mirror [http://www.sa-update.pccc.com/](http://www.sa-update.pccc.com/) weight=5
Jul  9 11:26:00.731 [20148] dbg: channel: found mirror [http://sa-update.secnap.net/](http://sa-update.secnap.net/) weight=5
Jul  9 11:26:00.731 [20148] dbg: channel: found mirror [http://sa-update.space-pro.be/](http://sa-update.space-pro.be/) weight=1
Jul  9 11:26:00.731 [20148] dbg: channel: selected mirror [http://www.sa-update.pccc.com](http://www.sa-update.pccc.com)
Jul  9 11:26:00.732 [20148] dbg: http: url: [http://www.sa-update.pccc.com/1608691.tar.gz](http://www.sa-update.pccc.com/1608691.tar.gz)
Jul  9 11:26:00.732 [20148] dbg: http: downloading to: /var/lib/spamassassin/3.004000/updates_spamassassin_org/1608691.tar.gz, new
Jul  9 11:26:00.732 [20148] dbg: util: executable for curl was found at /usr/bin/curl
Jul  9 11:26:00.732 [20148] dbg: http: /usr/bin/curl -s -L -O --remote-time -g --max-redirs 2 --connect-timeout 30 --max-time 300 --fail -o 1608691.tar.gz -- [http://www.sa-update.pccc.com/1608691.tar.gz](http://www.sa-update.pccc.com/1608691.tar.gz)
Jul  9 11:26:01.102 [20148] dbg: http: process [20151], exit status: 5888
Jul  9 11:26:01.102 [20148] dbg: channel: selected mirror [http://sa-update.secnap.net](http://sa-update.secnap.net)
Jul  9 11:26:01.103 [20148] dbg: http: url: [http://sa-update.secnap.net/1608691.tar.gz](http://sa-update.secnap.net/1608691.tar.gz)
Jul  9 11:26:01.103 [20148] dbg: http: downloading to: /var/lib/spamassassin/3.004000/updates_spamassassin_org/1608691.tar.gz, new
Jul  9 11:26:01.103 [20148] dbg: util: executable for curl was found at /usr/bin/curl
Jul  9 11:26:01.103 [20148] dbg: http: /usr/bin/curl -s -L -O --remote-time -g --max-redirs 2 --connect-timeout 30 --max-time 300 --fail -o 1608691.tar.gz -- [http://sa-update.secnap.net/1608691.tar.gz](http://sa-update.secnap.net/1608691.tar.gz)
Jul  9 11:26:01.538 [20148] dbg: http: process [20153], exit status: 5888
Jul  9 11:26:01.538 [20148] dbg: channel: selected mirror [http://sa-update.dnswl.org](http://sa-update.dnswl.org)
Jul  9 11:26:01.539 [20148] dbg: http: url: [http://sa-update.dnswl.org/1608691.tar.gz](http://sa-update.dnswl.org/1608691.tar.gz)
Jul  9 11:26:01.539 [20148] dbg: http: downloading to: /var/lib/spamassassin/3.004000/updates_spamassassin_org/1608691.tar.gz, new
Jul  9 11:26:01.539 [20148] dbg: util: executable for curl was found at /usr/bin/curl
Jul  9 11:26:01.539 [20148] dbg: http: /usr/bin/curl -s -L -O --remote-time -g --max-redirs 2 --connect-timeout 30 --max-time 300 --fail -o 1608691.tar.gz -- [http://sa-update.dnswl.org/1608691.tar.gz](http://sa-update.dnswl.org/1608691.tar.gz)
Jul  9 11:26:01.651 [20148] dbg: http: process [20155], exit status: 5888
Jul  9 11:26:01.651 [20148] dbg: channel: selected mirror [http://sa-update.space-pro.be](http://sa-update.space-pro.be)
Jul  9 11:26:01.652 [20148] dbg: http: url: [http://sa-update.space-pro.be/1608691.tar.gz](http://sa-update.space-pro.be/1608691.tar.gz)
Jul  9 11:26:01.652 [20148] dbg: http: downloading to: /var/lib/spamassassin/3.004000/updates_spamassassin_org/1608691.tar.gz, new
Jul  9 11:26:01.652 [20148] dbg: util: executable for curl was found at /usr/bin/curl
Jul  9 11:26:01.652 [20148] dbg: http: /usr/bin/curl -s -L -O --remote-time -g --max-redirs 2 --connect-timeout 30 --max-time 300 --fail -o 1608691.tar.gz -- [http://sa-update.space-pro.be/1608691.tar.gz](http://sa-update.space-pro.be/1608691.tar.gz)
Jul  9 11:26:01.843 [20148] dbg: http: process [20157], exit status: 5888
channel: could not find working mirror, channel failed
Jul  9 11:26:01.843 [20148] dbg: generic: cleaning up temporary directory/files
Jul  9 11:26:01.844 [20148] dbg: generic: cleaning directory /tmp/.spamassassin20148LqkbM6tmp
Jul  9 11:26:01.844 [20148] dbg: diag: updates complete, exiting with code 4
sa-update failed for unknown reasons
```


I've spent a week or so rummaging around but haven't found any solutions, and nor have I tried to tweak anything for fear of breaking it. Does anyone have any thoughts please?

Many thanks


Jim

---

### Post by mobidyc-gmail on 2014-07-09
Hello,

I detected this problem today, it is a permission problem.
try to chown the /var/lib/spamassassin/* files with the appropriate user.

# chown -R debian-spamd:debian-spamd /var/lib/spamassassin

---

### Post by SeijiSensei on 2014-07-09
Maybe it's this bug: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=739373](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=739373)

---

### Post by jimwillsher on 2014-07-09
Thank you, both of you, for your replies. The post by mobidyc-gmail seems to have worked, I've run the command manually and this time it's exited with 0.

Thanks again


Jim

---

### Post by robert138 on 2014-11-17
This post has been extremely helpful.  I spent many hours troubleshooting the problem and found the solution here.  [[COLOR=#000000]mobidyc-gmail[/COLOR]]("http://ubuntuforums.org/member.php?u=1933356") was on target.... Thanks

---

