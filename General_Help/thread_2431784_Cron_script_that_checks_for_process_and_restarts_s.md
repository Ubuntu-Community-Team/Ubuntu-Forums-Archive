---
title: "Cron script that checks for process and restarts system"
date: 2019-11-21
forum: General Help
---

### Post by bomberb17 on 2019-11-21
Hello, I am running Ubuntu server 18.04LTS and I have a process running with screen in the background. Sometimes this process gets stopped (I can't find why at the moment) so as a temporary solution I am trying to write a cron script that reboots the server so that the process starts again. 

Here is the root crontab:
```
@reboot ( sleep 90 ; sh /home/user/startscript.sh )

```
Here is the startscript

```
DEFAULT_DELAY=0
if [ "x$1" = "x" -o "x$1" = "xnone" ]; then
   DELAY=$DEFAULT_DELAY
else
   DELAY=$1
fi
sleep $DELAY

su user-c 'cd ~/myfolder/ && screen -dmS node node server && sleep 10 && screen -dmS npm npm start'
```


The script that checks the process is as follows:

```
#!/bin/bash
if ! screen -ls |grep node > /dev/null
then
    systemctl reboot -i
fi
```

And this script is run by a user cronjob
```
52 * * * * /home/user/check.sh
```

The problem now is that the process is run as a user, who however does not have privileges to restart the system (so the check.sh script fails to restart the system).
Can someone suggest a solution?
Thanks!

---

### Post by Tadaen_Sylvermane on 2019-11-21
Why not just restart the service. Rebooting should be rarely needed. Certainly not to reload a service.

Run these with an @reboot as the regular user in crontab and they will check every 30 seconds if the screen sessions are active. if not, runs startup, else just waits another 30 seconds. probably better ways to do this but this is what I came up with in a minute. No sudo or root required. I don't see the point of your delay personally but squeeze it in if you need it. both of these will do the job.

```
while true ; do
    if ! screen -ls | grep node > /dev/null ; then
        cd /home/"$USER"/myfolder
        screen -dmS node node server
    fi
    sleep 10
    if ! screen -ls | grep npm > /dev/null ; then
        cd /home/"$USER"/myfolder
        screen -dmS npm npm start
    fi
    sleep 30
done
```

or with a function so you can use the same block. always good to use recyclable code when it will be repeated instead of hard coding each line.

```
screen_starter() {   
    if ! screen -ls | grep "$1" ; then
        cd /home/"$USER"/myfolder && screen -dmS "$1" "$1" "$2"
        sleep 10
    fi
}
while true ; do
    screen_starter node server
    screen_starter npm start
    sleep 30
done
```

this is little more than a hack though. you need to find the source of the crash and fix that mainly. as a rule services should not randomly just die. this is linux, not windows. i run something similar to the above with my minecraft servers. i also have email alerts if they go down. i haven't gotten an email or a failed server for as long as I've been running them though. they simply don't die. don't accept mediocrity from whatever you are running.

---

### Post by bomberb17 on 2019-11-21
Thanks for your input, I think that if npm dies I have to kill node before starting both again (and vice versa) but try your script and see what happens when one of them dies again.
Yes I need to figure out why they die, just need to find the time to do it..

---

