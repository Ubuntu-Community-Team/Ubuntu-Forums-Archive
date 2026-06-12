---
title: "problem with nrpe and ubuntu"
date: 2017-10-10
forum: General Help
---

### Post by majed17 on 2017-10-10
Peace,
I tried to add a command to nrpe.cfg and restart nrpe but on the remote machine it would write 
Code: [Select all]("https://support.nagios.com/forum/viewtopic.php?f=35&t=45930&p=234739#")check_service not defined
i checked if there are other nrpe.cfg files but there aren't. I restarted the server and voila, it worked!
it means the nrpe demon is not restarting on ubuntu.
Version: 2.15
when is ubuntu going to update nrpe to the latest version?

---

### Post by Kirboosy on 2017-10-10
I use the following to restart NRPE Server
```
sudo systemctl restart nagios-nrpe-server
```
> when is ubuntu going to update nrpe to the latest version?
If you need the newer functionality of later versions newer version of Ubuntu run more current software.
17.04 NRPE: 3.0.1
17.10 NRPE: 3.2.0

If you need to stay on 16.04 you could build your own packages of NRPE and host it on launchpad :)

~Caboose

---

### Post by majed17 on 2017-10-11
is there a way to update to Ubuntu 17 without installing fresh?

Also, I installed a new ubuntu test server and install nrpe but it gets compiled without ssl support, how to install it with ssl support?

---

### Post by Kirboosy on 2017-10-13
> **majed17 said:**
> is there a way to update to Ubuntu 17 without installing fresh?

Yes, please look at this guide: [Upgrading - Ubuntu Wiki]("https://help.ubuntu.com/lts/serverguide/installing-upgrading.html")

> **majed17 said:**
> [COLOR=#000000]Also, I installed a new ubuntu test server and install nrpe but it gets compiled without ssl support, how to install it with ssl support?[/COLOR]

Make sure that you have the package [libssl-dev]("https://packages.ubuntu.com/search?keywords=libssl-dev") installed when you run your configure. If you don't it will compile NRPE without SSL support.

~Caboose

---

### Post by majed17 on 2017-10-30
thank you for helping, I had libssl-dev installed and it would still compile without ssl, anyway it was solved when i updated to 17.10
I tried 
do-release-upgrade -d
but it produces an error:
:~$ do-release-upgrade -d
Checking for a new Ubuntu release
ERROR:root:parse failed for '/home/sysadmin/.cache/update-manager-core/meta-release-lts-development'
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 240, in parse
    while index_tag.step():
SystemError: E:&#1053;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1088;&#1072;&#1079;&#1086;&#1073;&#1088;&#1072;&#1090;&#1100; &#1089;&#1086;&#1076;&#1077;&#1088;&#1078;&#1080;&#1084;&#1086;&#1077; &#1092;&#1072;&#1081;&#1083;&#1072; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072;  (1)

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 372, in download
    self.parse()
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 278, in parse
    self.METARELEASE_URI)
UpdateManager.Core.MetaRelease.MetaReleaseParseError: Unable to parse [http://changelogs.ubuntu.com/meta-release-lts-development](http://changelogs.ubuntu.com/meta-release-lts-development)
Upgrades to the development release are only
available from the latest supported release.

python3 is installed!

---

