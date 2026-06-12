---
title: "dpkg: error processing freepats (--configure):"
date: 2013-01-19
forum: General Help
---

### Post by natespapa09 on 2013-01-19
I keep getting the following error when trying to install anything. I installed Chrome (not Chromium) first thing and it was fine. But upates through apt-get and restricted extra through apt-get don't seem to install I get the following message. 

Do you want to continue [Y/n]? y
Get:1 [http://packages.medibuntu.org/](http://packages.medibuntu.org/) quantal/non-free libavutil-extra-51 amd64 6:0.8.4ubuntu0.12.10.1+medibuntu1 [106 kB]
Fetched 106 kB in 9s (11.6 kB/s)                         
(Reading database ... 152897 files and directories currently installed.)
Preparing to replace libavutil-extra-51:amd64 6:0.8.4ubuntu0.12.10.1 (using .../libavutil-extra-51_6%3a0.8.4ubuntu0.12.10.1+medibuntu1_amd64.deb) ...
Unpacking replacement libavutil-extra-51:amd64 ...
[COLOR="Red"]dpkg: error processing freepats (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.[/COLOR]
Setting up libavutil-extra-51:amd64 (6:0.8.4ubuntu0.12.10.1+medibuntu1) ...
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 freepats
E: Sub-process /usr/bin/dpkg returned an error code (1)
rob@ubuntu:~$ 

I installed Ubuntu with WUBI on a 64 bit windows 7 machine.

---

### Post by ibjsb4 on 2013-01-20
What happens when you reinstall [COLOR=Red]freepats  
[/COLOR]

---

### Post by iponeverything on 2013-01-20
what he said -- run it from terminal, it might be easier to spot the issue.

cd /var/cache/apt/archive
sudo dpkg -i freepats*

---

### Post by natespapa09 on 2013-02-13
I fixed it the hard way. I uninstalled Wubi and installed Ubuntu directly from DVD. No problems now. I have read several posts that stated Wubi is not the way to go and after this I would have to agree.

---

