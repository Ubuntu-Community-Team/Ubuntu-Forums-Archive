---
title: "Xsane &quot;Failed to open device&quot; on 64 bit ubuntu 16.10, but sane-utils work."
date: 2017-02-19
forum: General Help
---

### Post by axe87 on 2017-02-19
I recently migrated to ubuntu 64 bit and everything is working fine except xsane. In xsane I'm getting the "Failed to open device`pixma:MX530_192.168.2.113`: Invalid argument." error.  However, sane-find-scanner scanimage seem to work fine. Also, the Canon scangearmp tool works fine.

This used to work on the 32bit version.

I have a suspicion there is something wrong with the 64 bit installation of xsane. When I do a which on scanimage it shows as a 32bit executable whereas xsane is 64 bit. I've tried uninstalling and reinstalling but with the same results.

---

### Post by axe87 on 2017-02-25
I'm trying to completely purge sane and xsane but for some reason the sane-utils executables remain eventhough the package is apparently removed.

---

### Post by axe87 on 2017-03-01
OK fixed, after managing to purge out the old 32 bit version of sane / xsane, I found the answer here [http://askubuntu.com/questions/688642/network-scanner-canon-stops-after-upgrade-from-15-04-to-15-10](http://askubuntu.com/questions/688642/network-scanner-canon-stops-after-upgrade-from-15-04-to-15-10) and used the solution of copying in the experimental libs.

---

