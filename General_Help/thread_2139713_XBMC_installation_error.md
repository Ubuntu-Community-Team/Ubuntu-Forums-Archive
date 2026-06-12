---
title: "XBMC installation error"
date: 2013-04-27
forum: General Help
---

### Post by wazobia on 2013-04-27
Hello.

I am currently using Ubuntu 12.10. Not the most advanced user out there, and my knowledge of errors are not so great

Here's the problem. I'm currently trying to install xbmc on my machine (Samsung series 9 laptop), and I keep getting errors when it's unpacking (this install is from the software centre):

nstallArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 320953 files and directories currently installed.)
Unpacking xbmc-bin (from .../xbmc-bin_3%3a12.1-1~ppa1~quantal_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/xbmc-bin_3%3a12.1-1~ppa1~quantal_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/xbmc/addons/pvr.mythtv.cmyth/XBMC_MythTV_cmyth.pvr', which is also in package xbmc-pvr-mythtv-cmyth 1.7.10-2quantal
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking xbmc (from .../xbmc_3%3a12.1-1~ppa1~quantal_all.deb) ...
dpkg: error processing /var/cache/apt/archives/xbmc_3%3a12.1-1~ppa1~quantal_all.deb (--unpack):
 trying to overwrite '/usr/share/xbmc/addons/pvr.vdr.vnsi/addon.xml.in', which is also in package xbmc-pvr-vdr-vnsi 1.7.4-2quantal
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xbmc-bin_3%3a12.1-1~ppa1~quantal_amd64.deb
 /var/cache/apt/archives/xbmc_3%3a12.1-1~ppa1~quantal_all.deb
Error in function: 


Anybody ever have the same issue, or know the solution to this problem? I have searched around on forums but cannot see...maybe my search terms are not the best!

Thanks.

---

