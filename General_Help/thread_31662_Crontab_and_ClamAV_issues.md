---
title: "Crontab and ClamAV issues"
date: 2005-05-04
forum: General Help
---

### Post by Takis on 2005-05-04
I have a small batch file that I've set my crontab to scan my hdd weekly (it shows here as nightly, because I'm trying to get it to work properly)
```
30 2 * * *      /home/me/bin/scan
```
The scan file has a number of small things to do, but the main one is to run
```
clamscan -ri / >> ~/clamscan.log
```
The cron job runs okay, but nothing gets printed out by clamscan (normally there's a couple of diagnostic pieces of info). I timestamp before and after the clam job is run, and the difference is 1 second. I know the script works because I can run the script myself and it works, the timestamp difference is about 2 hours. Any ideas?  ](*,)  TIA

---

### Post by Takis on 2005-05-08
bump

---

