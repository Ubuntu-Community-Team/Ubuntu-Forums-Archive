---
title: "cron"
date: 2008-04-23
forum: General Help
---

### Post by cheeseman557 on 2008-04-23
hi,

i want to automatically open a text file everyday at 4:30pm.

i added this command to crontab, but it didnt launch it:

```

30 16 * * *  gedit /media/sda5/pushups.txt

```

the path is correct, and when i run the command in terminal, it works fine.
is there something wrong with it?
thanks!

---

### Post by ibuclaw on 2008-04-23
The purpose of cronjobs are really to run commandline processes in the background without bothering you,

ie:
00 *  * * *  apt-get update && apt-get upgrade || echo "No Connection"

Will do hourly updates and upgrades of my repository. Without the nuance of me worrying about it myself.


If you want a file to be opened every day at 4:30
I recommend using your login scripts to do the job.

ie:
```
gedit /media/sda5/pushups.job
```
Then paste this into the file:
```

#!/bin/bash

### Set your time here ###
alarm_hour="16"
alarm_minute="30"
alarm_second="00"
#########################

set-alarm()
{
export current_hour=$1
export current_minute=$2
export current_second=$3

    if [ "$alarm_hour" -lt "$current_hour" ]
    then
        export set_hour=$(($alarm_hour + 24 - $current_hour))
    else
        export set_hour=$(($alarm_hour - $current_hour))
    fi

    if [ "$alarm_minute" -lt "$current_minute" ]
    then
        export set_minute=$(($alarm_minute + 60 - $current_minute))
        let "set_hour--"
    else
        export set_minute=$(($alarm_minute - $current_minute))
    fi

    if [ "$alarm_second" -lt "$current_second" ]
    then
        export set_second=$(($alarm_second + 60 - $current_second))
        let "set_minute--"
    else
        export set_second=$(($alarm_second - $current_second))
    fi
sleep "$set_hour"h "$set_minute"m "$set_second"s
}

export time=$(date | awk '{print $4}' | sed 's/:/ /g')
set-alarm $time
gedit /media/sda5/pushups.txt
exit 0

```
Mark the file as executable
```
chmod +x /media/sda5/pushups.job
```
Then edit your PostLogin file.
```
gksu gedit /etc/gdm/PostLogin/Default
```
Paste this into that file:
```

#!/bin/bash

if [ -x /media/sda5/pushups.job ]
then
    cd /media/sda5/
    exec ./pushups.job &
fi
exit 0

```
Save and Quit.
And change the permissions to execute on that file too.
```
sudo chmod +x /etc/gdm/PostLogin/Default
```

And you are all set!

NOTE: Because of the way I wrote the script. This will only run the script once per login. If you're logged in for more than 24 hours, it won't open the file the second time round.

[EDIT]: For this to work, you need to log out and log back in again.

Regards
Iain

---

### Post by cheeseman557 on 2008-04-23
oh wow thanks! ive been looking for a quick simple way to remind myself to do pushups everyday, and i used scheduled tasks in windows to open up a txt file everyday to prod me into doing it. this is just about gonna complete my shift over to ubuntu! thanks a lot! :D i really appreciate it. little things like this just make my day. thanks again! :)

---

### Post by ibuclaw on 2008-04-23
Oh, if that's all you want, perhaps you should consider an alarm applet?
[http://joh.deworks.net/blog/?page_id=58](http://joh.deworks.net/blog/?page_id=58)
It can make noises and open a notification window on screen.

Requires compiling.
But just follow the instructions on the page.
And when you've done, right click the gnome panel and select "Add to Panel"

Regards
Iain

---

