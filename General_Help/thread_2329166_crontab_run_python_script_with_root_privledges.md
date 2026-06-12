---
title: "crontab run python script with root privledges"
date: 2016-06-28
forum: General Help
---

### Post by zach-holbrook02 on 2016-06-28
I need to run a python script at a certain time each day. The catch is I am not logged in as root but the script needs to be ran as root or at least I think so, because it accesses some files  that are for some reason locked. Below is what I have added to crontab and I get the logs.txt output every 5 minutes but it is blank as the script did not run I imagine. I have tried running with and without sudo but have not been successful. I currently manually run the file by using "sudo python checker2.py" and imputting the password. I also am open to any other suggestions such as cron but I have no experience with it. Other just single scripts that do not access other files run just fine.

5 * * * * /usr/bin/python sudo checker2.py >> logs.txt

---

### Post by steeldriver on 2016-06-28
Hello and welcome to the forums

To run a cron job as root, it should be sufficient to put it in root's crontab

```

sudo crontab -e

```

(instead of plain crontab -e). Then remove all references to sudo within the crontab - but remember to give full paths to the script and to the output file

```

5 * * * * /usr/bin/python /path/to/checker2.py >> /path/to/logs.txt

```

(the `/path/to/` parts need not be the same - for example you could put the log in your /home/user/ directory but keep checker2.py in /usr/local/bin).

If checker2.py is executable and has the appropriate 'shebang', you shouldn't need to invoke the interpreter directly, just

```

5 * * * * /path/to/checker2.py >> /path to/logs.txt

```

---

### Post by Impavidus on 2016-06-28
Files are for some reason locked so you *think* you need root privileges. You don't sound very sure. You'd better know exactly why you need root permissions before you try and use them. You understand file permissions?
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Sure, there can be very legitimate reasons to run a script periodically with root permissions. The way to do that is to put it in root's crontab. That's better than putting it with a sudo command in your own crontab. And because of the very limited environment for commands in crontab, it's best to always use absolute paths. So change the path of the log file and to the python script to an absolute path. Note that if you put the command in root's crontab, the log file will be owned by root.

---

### Post by papibe on 2016-06-28
Hi zach-holbrook02.

If you created the crontab using the root account, for instance:
```
sudo crontab
```
you don't need to put sudo in the command itself, as it would run as root already. This would suffice:
```
5 * * * * /usr/bin/python /path/to/checker2.py >> /path/to/logs.txt  2>&1
```
Note that you may avoid common problems if you use absolute paths. Also, I recommend redirecting the standard error to your log too (good for debugging).

That should work unless there's something either interactive or that requires the tty.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by zach-holbrook02 on 2016-06-30
It is not using the root account that is why sudo and the password is required. the above code is what I have been trying to run but does not work.

---

### Post by zach-holbrook02 on 2016-06-30
I have made the tab under the root user but it just will not run the script without either being logged in as root or providing sudo and the password.

---

### Post by papibe on 2016-06-30
Is there anything either interactive or that requires the tty on the script?

Could you post the content of the script?

Regards.

---

### Post by zach-holbrook02 on 2016-07-05
Its a massive script, that pulls in files and compares data. But nothing that requires interaction.

---

### Post by papibe on 2016-07-06
Try this tricks to debug the issue:
```
import time

def log(msg):
    timenow = time.localtime()
    nowstr = time.strftime("%Y-%d-%d %H:%M:%S", timenow)
    print("{}: {}".format(nowstr, msg))
...
log('Starting')
....
log('Doing X')
...
log('After X')
...
log('Before Y')
..

```
You get the idea? Then you can take a look at the log and see where the program is failing.

by the way, we may have misinterpreted how often you want to run the script. Every 5 minutes should something like this
```
**[COLOR="#FF0000"]*/5[/COLOR]** * * * * /usr/bin/python /path/to/checker2.py >> /path/to/logs.txt  2>&1
```
Hope it helps. Let us know how that goes.
Regards.

---

