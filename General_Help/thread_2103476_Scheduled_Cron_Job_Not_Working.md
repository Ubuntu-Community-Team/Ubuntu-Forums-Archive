---
title: "Scheduled Cron Job Not Working"
date: 2013-01-10
forum: General Help
---

### Post by patdundee on 2013-01-10
Hi Guys
Ubuntu Server 12.04.1
Being new to cron jobs, I have used webmin to set a custom job up. I have checked via cmd line using crontab -e and it is also in there.
I can run the cron job manually via webmin and it runs fine. The job is active and set to run every 30 minutes.

Problem is it does not auto run. The job is set up to run as Root user. It is a PHP job that usies a MySql connection and all connections and includes required are accessable

Here is the setting
php /home/websiteaddress/ServerBuildCountyService.php /dev/null

After manual running via webmin this is the output 
Output from command php /home/websiteaddress/ServerBuildCountyService.php /dev/null ..
Phase1 completePhase2 complete

And everything is updated

Any help would be greatly appreciated.

---

