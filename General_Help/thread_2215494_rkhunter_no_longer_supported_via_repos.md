---
title: "rkhunter no longer supported via repos?"
date: 2014-04-06
forum: General Help
---

### Post by Psil0cybin on 2014-04-06
I am using **Xubuntu 12.04 LTS**, I usually used **Rootkit Hunter version 1.3.8** without a hitch, today I attempted to update the program , and was getting the following error.


> 
[22:19:21]  Info: Executing download command '/usr/bin/wget  -q -O  /var/lib/rkhunter/tmp/rkhunter.upd.eA8q1aBmwi  [http://rkhunter.sourceforge.net/1.3/i18n/1.3.8/i18n.ver](http://rkhunter.sourceforge.net/1.3/i18n/1.3.8/i18n.ver) 2>/dev/null'
[22:19:31] Checking file i18n versions                       [ Update failed ]
[22:19:31] Warning: Download of 'i18n.ver' failed: Unable to determine the latest version number.
[22:19:31]


I  have come to the conclusion that the rkhunter that is provided in the  default ubuntu repos is outdated, after reading a few posts online.
As well as, attempting to access the file using my browser (receiving a error 404)

> 
1. **Server:** rkhunter.sourceforge.net 
2. **URL path:** /1.3/i18n/1.3.8/i18n.ver 
3. **Error notes:** NONE 
4. **Error type:** 404 
5. **Request method:** GET 
6. **Request query string:** NONE 
7. **Time:** 2014-04-07 03:52:26 UTC (1396842746)


I was wondering if I happen to update from the official website (sourceforge site, using the tar.gz), will that over write the current rkhunter install, or will it install rkhunter in various other folders, causing two instances to be installed?

If that is the case, should I
A) Wait for an update to be provided via the Ubuntu repos?
B) Purge remove rkhunter and install it via the source file?

---

