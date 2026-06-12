---
title: "Files run when certain time every day."
date: 2012-11-24
forum: General Help
---

### Post by Raafat1991 on 2012-11-24
Hi guys


In ubuntu i want a command for knowing all files that automatically run when certain time every day.


thanks....

---

### Post by SeijiSensei on 2012-11-24
By default, the only things that run on schedules are stored in the /etc/cron.* directories.  /etc/cron.daily contains the programs that run each night.

For more understanding of how scheduled tasks work in Linux read: [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by The Cog on 2012-11-24
I think the prime command would be
```
sudo cat /etc/crontab
```
but that will just show you when it runs all the files in /etc/cron.hourly, /etc/cron.daily, /etc/cron.weekly.

---

### Post by Raafat1991 on 2012-11-25
Hi , i think that [COLOR=Blue]crontab -l [/COLOR] it's what i want.

thank you  [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195")  [[COLOR=#DD4814]**The Cog .**[/COLOR]]("http://ubuntuforums.org/member.php?u=437760")

---

