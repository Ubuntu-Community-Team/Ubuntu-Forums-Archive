---
title: "service restart through cron job  problem"
date: 2008-05-28
forum: General Help
---

### Post by cooldevil009 on 2008-05-28
HI.......

I am facing a weired problem while using cron job.
I want to check if nis is running every 1 min and restart it if not running.
I am starting it using
/etc/init.d/nis restart. it works when i execute the script in terminal but doesn't work thru cron job. my other setup is fine. In my script, I am creating a folder in a directory to check whether it is running fine or not. The folder gets created after 1 min. but nis doen't start.
I tried 
/etc/init.d/nis stop 
and then 
/etc/init.d/nis start
but no help. 
Even just "/etc/init.d/nis stop" doesn't stop nis.
What could be the reason??

---

### Post by bingoUV on 2008-05-28
To troubleshoot, try the following in your cron tab
```

/etc/init.d/nis stop 2>> /path/to/log/file

```

Wait for cron to run it. Does something get appended to the file, or did the file get created? It might contain the error. 

If it does not do anything to your log file, something is wrong with your cron time specification.

---

### Post by kpkeerthi on 2008-05-28
You should be adding these commands to root's cron. Aren't you?

---

