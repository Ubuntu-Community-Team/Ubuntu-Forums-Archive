---
title: "Problem running script as $USER"
date: 2013-09-30
forum: General Help
---

### Post by sil3nthunt3r on 2013-09-30
Hi all,

I have problem to run the following script as user ($USER).
I have setup cronjob to run the script every 3 minutes.

Basically, the script will check the running process for the user and start the process as the user if the process is not running.

```
#!/bin/sh
PATH=/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/bin:/sbin
SERVICE='irssi'
HOMEDIR="/home/$USER"
SIZE=95 #total %age


df $HOMEDIR| tail -1 | while read fs size used avail pcnt mount;
do
  pcnt=$(echo ${pcnt} | cut -d'%' -f1 )
  if [ ${pcnt} -ge $SIZE ]; then
    echo "Running out of space \"${fs} (${pcnt}%)\" on ${HOSTNAME} as on $(date)"
    exit 1
  fi


if pgrep -u $USER $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    echo "$SERVICE is not running, starting $SERVICE" && screen -d -m -S testscript $SERVICE
fi
done
```

I name the script as chkirssi, chmod 777 the script.

When I check the cronjob log, I can see there's an error as below:
***pgrep: invalid user name: irssi***

I have change the $USER to $LOGNAME, same error occur.

I setup the cronjob for the user as below:

sudo crontab -u sil3nthunt3r -e

@reboot     /usr/local/bin/chkirssit >/dev/null 2>&1
@reboot    /usr/bin/screen -D -m /usr/local/bin/rtorrent
*/3 * * * *    /usr/local/bin/chkirssi >>/home/sil3nthunt3r/log.txt 2>&1


Kindly need your input on this.

Thanks

---

### Post by Vaphell on 2013-09-30
looks like $USER is null.
```
$ user=''
$ pgrep -u $user irrsi
pgrep: invalid user name: irrsi
```

Btw, do yourself a favor and always quote your variables.

---

### Post by sil3nthunt3r on 2013-09-30
> **Vaphell said:**
> looks like $USER is null.
```
$ user=''
$ pgrep -u $user irrsi
pgrep: invalid user name: irrsi
```

Btw, do yourself a favor and always quote your variables.

Hi,

$USER variable suppose to grab the username of the user from the system correct?
This script run in multiuser environment where each user have their own crontab that will run this script.
That is why $USER is being use. But not sure why it did not work.

---

### Post by Vaphell on 2013-09-30
do a test - echo $USER and other important variables to your log.txt file to see if you work with what you think you work with.

---

### Post by Lars Noodén on 2013-09-30
For whatever reason, $USER is not one of the environment variables set in cron.  
$LOGNAME is set, however.  It might be useful to have your script verify that one or the other of those variables is available before passing them on to other programs.

You can see all of what is available to you in cron by adding a cronjob like this:

```

set > /tmp/sil3nthunt3r

```

Then check the contents of that file after the cron job has run.

---

### Post by CaptainMark on 2013-09-30
Crontabs only inherit a very basic environment with next to no preset variables, you can set $USER in your crontab if you want to specify it, just put it above your script entry because crontabs are evaluated in a linear fashion

---

