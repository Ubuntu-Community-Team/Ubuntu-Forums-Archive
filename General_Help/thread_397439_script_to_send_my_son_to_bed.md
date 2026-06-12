---
title: "script to send my son to bed"
date: 2007-03-30
forum: General Help
---

### Post by jmvidalvia on 2007-03-30
My son is 11 years old, and uses to play enemy territory in our family laptop (kubuntu dapper) every day for one hour. He is an excelent student, so nothing to say.
The problem appears at 21:30, time to go to bed.
I need to make a script able to check the system time every 5 minutes, and send *sudo ifconfig eth0 down* if it is later than 21:30.
I know how to write in this scrip to start eth0, I just need help to have the script open checking the time recursively.
The day he is skilled enough to modify the script, he will be free to play as much as he wants.
I know it's is linux, not just Ubuntu, but now I really need the help of the comunity :) 
Thanks a lot!

---

### Post by yabbadabbadont on 2007-03-30
Setup a root cronjob to run at 21:30 every day that runs that command.  (without sudo, not needed if it is from root's crontab)

Of course, the best solution is to walk into the other room and tell him to go to bed...  ;)

---

### Post by ardchoille42 on 2007-03-30
> **jmvidalvia said:**
> My son is 11 years old, and uses to play enemy territory in our family laptop (kubuntu dapper) every day for one hour. He is an excelent student, so nothing to say.
The problem appears at 21:30, time to go to bed.
I need to make a script able to check the system time every 5 minutes, and send *sudo ifconfig eth0 down* if it is later than 21:30.
I know how to write in this scrip to start eth0, I just need help to have the script open checking the time recursively.
The day he is skilled enough to modify the script, he will be free to play as much as he wants.
I know it's is linux, not just Ubuntu, but now I really need the help of the comunity :) 
Thanks a lot!

#!/bin/bash
echo "Time for bed" >> child_process
touch bedtime_story
sleep
exit

I'm just in a good mood today and thought this might bring a smile to your face :)

---

### Post by jmvidalvia on 2007-03-30
Thank's!
Thats a nice and simple idea, but my son is clever enought to restart the computer. If he does at 21:31, no cronjob will run.
That's why I thought about checking the time recursively: he just would be able to play a couple of minutes, which doesn't make any sense for him.
Yes, telling him to go to bed would be fine, but I got a system error from his kernel [-(
:)

---

### Post by r4ik on 2007-03-30
Other solution our youngest daughter 13 now.
Age 11 we let her play every minute in her spare-time.
When bedtime came and schoolwork was done we left her free.
Took 5 days before she made up her mind and wanted to go to bed normal time :)

---

### Post by stylishpants on 2007-03-31
> **jmvidalvia said:**
> Thank's!
Thats a nice and simple idea, but my son is clever enought to restart the computer. If he does at 21:31, no cronjob will run.
That's why I thought about checking the time recursively: he just would be able to play a couple of minutes, which doesn't make any sense for him.
Yes, telling him to go to bed would be fine, but I got a system error from his kernel [-(
:)

If he restarts the computer, then your script will stop running anyway.

How about having the cron job run every few minutes between 21:30 and 22:00?

Run "sudo crontab -e" and enter this:

```

30-59/2 21 * * * ifdown eth0
0 22 * * * ifup eth0

```

This runs the command every two minutes, starting at 21:30, ending at 21:59.  Then at 22:00, it brings up eth0 again.


If you are working on the system yourself some time when this kicks in, then you would want to temporarily disable this by running "sudo crontab -e" again and commenting out the line with a #.  (Remember to uncomment it again later!)

---

### Post by jmvidalvia on 2007-03-31
@stylishpants:
Yes, yours is a good solution.
Anyway, about initial idea, "my" script wouldn' stop after reseting because network wolud only be available through the same script. I would uncheck the automatic network loading and run my script with:

#!/bin/sh
ifconfig eth0 up
iwconfig eth0 essid xxxxxxx key s:xxxxxx
ifconfig eth0 192.168.1.2 netmask 255.255.255.0 broadcast 192.168.1.255
route add default gw 192.168.1.1
echo "nameserver xx.xx.xx.xx" > /etc/resolv.conf

**(here I need: if time >21:30, then ifconfig eth0 down, otherwise, keep checking)**

No script, no network. 
;)

Obviously, I will have a different script to mount the network.

I will try to learn a little bit more about crontab.
Many thanks!

---

### Post by PlancksCnst on 2007-03-31
Most homes these days have a router.  Frequently, this router will allow you to block ports (or access altogether) at specific times and days.  Look through your router software to see if you can do this.

---

### Post by jmvidalvia on 2007-03-31
Got it!
First script (mountnet.sh):

#!/bin/sh
ifconfig eth0 down
ifconfig eth0 up
iwconfig eth0 essid xxxxxxxx key s: xxxxxxx
dhclient eth0
ifconfig eth0 netmask 255.255.255.0 broadcast 192.168.1.255
/home/me/scripts/checktime.sh

second script (checktime.sh):

#!/bin/sh
while [ `date +%H%M` -lt 2130 ]; do
sleep 60
done
ifconfig eth0 down



Time to go to bed, now! :)

---

