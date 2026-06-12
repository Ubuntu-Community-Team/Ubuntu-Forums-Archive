---
title: "error processing package geoip-database-contrib"
date: 2019-06-25
forum: General Help
---

### Post by albert-whale on 2019-06-25
I am running Ubuntu 18.10, I am attempting to install wireshark, and have a problem with the following package:

```
sudo apt install geoip-database-contribReading package lists... Done
Building dependency tree       
Reading state information... Done
geoip-database-contrib is already the newest version (1.19).
0 upgraded, 0 newly installed, 0 to remove and 467 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Setting up geoip-database-contrib (1.19) ...
Downloading: http://geolite.maxmind.com/download/geoip/database/GeoLiteCountry/GeoIP.dat.gz
Failed to download http://geolite.maxmind.com/download/geoip/database/GeoLiteCountry/GeoIP.dat.gz
Downloading: http://geolite.maxmind.com/download/geoip/database/GeoIPv6.dat.gz
Failed to download http://geolite.maxmind.com/download/geoip/database/GeoIPv6.dat.gz
Downloading: http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz
Failed to download http://geolite.maxmind.com/download/geoip/database/GeoLiteCity.dat.gz
Downloading: http://geolite.maxmind.com/download/geoip/database/GeoLiteCityv6-beta/GeoLiteCityv6.dat.gz
Failed to download http://geolite.maxmind.com/download/geoip/database/GeoLiteCityv6-beta/GeoLiteCityv6.dat.gz
Downloading: http://geolite.maxmind.com/download/geoip/database/asnum/GeoIPASNum.dat.gz
Failed to download http://geolite.maxmind.com/download/geoip/database/asnum/GeoIPASNum.dat.gz
Downloading: http://geolite.maxmind.com/download/geoip/database/asnum/GeoIPASNumv6.dat.gz
Failed to download http://geolite.maxmind.com/download/geoip/database/asnum/GeoIPASNumv6.dat.gz
update-alternatives: error: alternative path /usr/share/GeoIP/GeoLiteCity.dat doesn't exist
dpkg: error processing package geoip-database-contrib (--configure):
 installed geoip-database-contrib package post-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 geoip-database-contrib



```

I have found two bug reports:

[https://bugs.launchpad.net/ubuntu/+source/geoip-database-contrib/+bug/1824160](https://bugs.launchpad.net/ubuntu/+source/geoip-database-contrib/+bug/1824160)
[https://bugs.launchpad.net/ubuntu/+source/geoip-database-contrib/+bug/1811029](https://bugs.launchpad.net/ubuntu/+source/geoip-database-contrib/+bug/1811029)

Neither of these discusses how to reolve this issu so that I can install wireshark.

I would like to keep the geoip database, so If I need to implement a Manual install, can someone please let me know where the Manual is, I will RTFM.

Thank you.

---

### Post by oldos2er on 2019-06-25
Visiting the website [https://dev.maxmind.com/geoip/geoip2/geolite2/](https://dev.maxmind.com/geoip/geoip2/geolite2/) reveals "GeoLite Legacy databases were discontinued on January 2, 2019" followed by a link [https://support.maxmind.com/geolite-legacy-discontinuation-notice/](https://support.maxmind.com/geolite-legacy-discontinuation-notice/)

I would imagine this is the source of the problem.

---

### Post by albert-whale on 2019-06-26
Can I fix the URLs I have found for the package?

---

### Post by oldos2er on 2019-06-26
Don't know why you couldn't give it a try.

---

