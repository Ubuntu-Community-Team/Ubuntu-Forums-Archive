---
title: "Crontab - &quot;1&quot; file at /root"
date: 2015-04-15
forum: General Help
---

### Post by brianhardy on 2015-04-15
I'm trying to get my crontab running for at least ntpdate.

As root, I have a crontab -e file with the following entry.

```
0 0 * * * ntpdate time.nrc.ca > /dev/null 2>1&
```

I've noticed it wasn't working, as when I manually updated the time, the drift was about 5 minutes (over several weeks)

Today I notice a file in /root, name "1"

Within this file is the following:
```
/bin/sh: 1: ntpdate: not found
```

What does this indicate?

---

### Post by Holger_Gehrke on 2015-04-15
It indicates two things:
1) The command in the crontab should have had "2>**&**1" to send error output to standard output (and thereby to /dev/null) (see 'man bash' for details, especially the section 'REDIRECTION')
2) You should give the full path to ntpdate (/usr/sbin/ntpdate I think) since the PATH during execution of the crontab seems to be different.

---

### Post by matt_symes on 2015-04-15
Hi

> ntpdate time.nrc.ca > /dev/null 2>1&

Just to clarify; this will pipe stdout into /dev/null and stderr into a file called 1. 

It will not use your environment but run under a restricted environment running as the user root (as you stated). This is why it wrote the file to /root. 

This restricted environment is what you want generally. It can be a useful security measure and is the reason why sudo sanitises its environment as well.

As pointed out, you can use full paths to the exes or you can add a PATH variable, and other variables, into the cron tab file itself.

Kind regards

---

### Post by brianhardy on 2015-04-15
That typo was the issue, after using full path it worked

---

