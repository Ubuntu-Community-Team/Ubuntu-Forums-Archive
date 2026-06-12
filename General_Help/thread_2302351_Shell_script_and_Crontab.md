---
title: "Shell script and Crontab"
date: 2015-11-09
forum: General Help
---

### Post by hannzin on 2015-11-09
Hi all,


I am in need of help.




I'm trying to create two scripts, one to run every 1 hour and one every 1 hour and a half. But I'm not getting the code seems functional.




vi /etc/check.sh


```
#!/bin/sh
SERVICE='vncserver'
 
if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE running, everything is fine"
else
	echo "$SERVICE is not running"
    su - root -c vncserver
fi

```

Permission


chmod 775 check.sh




Using crontab, I'm testing 5 minutes


crontab -e 
```
*/5 * * * * ./etc/check.sh 

```





vi /etc/check2.sh


```
#!/bin/sh
SERVICE='hitleap-viewer-browser'
 
if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    wine start "Z:\root\Desktop\hitleap-viewer-browser.exe"
fi

```	


Permission


chmod 775 check2.sh




Using crontab, I'm testing 7 minutes


crontab -e 
```
*/7 * * * * ./etc/check2.sh 

```

---

### Post by ian-weisser on 2015-11-09
Use full file paths. Cron has no idea where your ./etc is unless you explicity tell it so.
Cron is not you; it merely has permission to rummage through your files.

---

### Post by hannzin on 2015-11-09
Where Can I put the files? 

root? home?

---

### Post by branau on 2015-11-09
You can put the files wherever you like, you just have to specify the full path to them. So say you have the files in your home directory, your cron job should look like this:

```
*/5 * * * * /home/you/your-script.sh
```

Since it looks like you've got your stuff in the /etc/ directory, just remove the . at the beginning and they should work just fine

It's also a good idea to use the entire paths to each program you call in your script as well. So instead of grep, for example, you'd use 

```
/bin/grep
```

You can find the paths to these using the which command, like so:

```
which grep
```


On a side note, it isn't completely necessary to test your scripts with a cron job. If you run them from the terminal with the full paths, you can expect the outcome to be the same from the cron job, provided you aren't using sudo for anything (sudo cron tabs have to be run from the root user's crontab.)

---

### Post by SeijiSensei on 2015-11-10
I put programs that require root privileges in /usr/local/sbin, and ones that ordinary users can execute in /usr/local/bin.  /usr/local is the conventional location for programs and related files that are created outside of the basic distribution which uses the /usr tree.

---

