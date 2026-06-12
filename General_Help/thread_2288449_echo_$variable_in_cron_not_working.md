---
title: "echo $variable in cron not working"
date: 2015-07-27
forum: General Help
---

### Post by Sympatiko on 2015-07-27
Hi,


Im having trouble printing the result of the following when run by a cron. I have a script name under /usr/local/bin/test

```

#!/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin


ARAW=`date +%y%m%d`


NAME=`hostname`


TODAY=`date '+%D %r'`


cd /directory/bar/foo/


VARR=$(ls -lrt /directory/bar/foo/ | tail -1 | awk {'print $8'} | ls -lrt `xargs` | grep something)


echo "Resolve2 Backup" > /home/user/result.txt


echo " " >> /home/user/result.txt


echo "$VARR" >> /home/user/result.txt


mail -s "Result $TODAY" [email]email@email.com[/email] < /home/user/result.txt


```


I configured it in /etc/cron.d/test to run every 1am:
00 1 * * * root /usr/local/bin/test




When Im running it manually in command line
# /usr/local/bin/test
Im getting the complete value. But when I let cron do the work, it never display the part of echo "$VARR" >> /home/user/result.txt


Any ideas?


Thanks

---

### Post by Sympatiko on 2015-07-27
[FONT=Helvetica Neue] I solved my problem. The problem is the ouput of $8 and $9 in cron. I dont know what special field being read while it is being run in cron. Im just a newbie in scripting so sorry for my bad script =)[/FONT]

---

