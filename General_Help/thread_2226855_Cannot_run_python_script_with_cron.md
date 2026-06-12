---
title: "Cannot run python script with cron"
date: 2014-05-29
forum: General Help
---

### Post by sim085 on 2014-05-29
Hello, 

I have searched on the internet and to be honest the process to run a python script every five minutes seem to be quite strait forward. These are the steps I did: I went to */etc/cron.d* and created a file *myexp*. In myexp I pasted the following:

```

*/5 * * * * root /usr/bin/python /opt/myscript.py >> /opt/cronjob.log 2>&1


```

*(note I have a return character after first line as I read that this is required, i.e. - last line is empty)*

What happens is this. I get an empty file created in /opt named cronjob.log. 
Before I used to get a log entry in /var/logs/syslog but this does not work anymore (I think I saved the file when as root).
**My python script does not run**

I cannot understand what I am doing wrong. I tried to remove *>> /opt/cronjob.log 2>&1* and it does not workl. Looks at the various cron expressions. The fact that cronjob.log gets created makes me feel like the job is running but for some reason it is failing. However I cannot see what is failing!

---

### Post by sim085 on 2014-05-30
This works, problem was that I was only giving the name of the log file from the python script. This should be the full path, ex: /var/log/mylog.log

---

