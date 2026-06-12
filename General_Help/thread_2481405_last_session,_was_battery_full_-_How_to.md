---
title: "last session, was battery full? - How to"
date: 2022-11-28
forum: General Help
---

### Post by meetdilip on 2022-11-28
Hi, I often forget to charge the battery fully and switch off the laptop thinking that I will charge it to 100% the next time I plugin. Then I forget about it and continue using the battery from 60% or something till low battery. I am trying to put something up in Python ( or something else ) which can check whether the battery was full during the last session. 

What is the best way of doing it? Is there a default battery charge log available in 22.04? Does it show when the charge was 100% the last time?

Thanks.

---

### Post by TheFu on 2022-11-28
I have a little cron script that runs every hour and checks for the current battery level. Since my laptop gets 8+ hrs on a charge, I usually don't have it alarm until less than 30% remaining.  
```
$ more batt-chk.sh 
#!/bin/bash

# Battery 0: Not charging, 100
BATT=$(acpi -i |grep -v capacity \
|sed -e 's/^.*[cC]harging, //g' -e 's/\%.*$//' \
|sed -e 's/^.*Discharging, //g' -e 's/\%.*$//')

# echo \"$BATT\"

if [ 30 -ge $BATT ] ; then
   wall "==INFO== Low battery: $BATT"
   DISPLAY=:0 mpv /usr/share/sounds/ubuntu/stereo/phone-incoming-call.ogg
else
   echo "==INFO== Battery Level: $BATT %"
fi

```
For your consideration.  Don't know if 'acpi' works on your release or not.  'wall' is pretty hostile towards GUIs, so you'll likely want something else there and the audio is totally obnoxious.

---

### Post by meetdilip on 2022-11-29
Thanks. I have this code which alerts me if the battery is full. Is it possible to log every " battery full " occurrence somehow? It would be the easiest I guess. 

```
#!/bin/bash

while true; do
    state="$(awk '/state:/ {print $2}' <(upower -i /org/freedesktop/UPower/devices/battery_BAT0))"
    percentage="$(awk '/percentage:/ {print 0+$2}' <(upower -i /org/freedesktop/UPower/devices/battery_BAT0))"
    [ "$state" == "charging" ] && [ "$percentage" -ge "95" ] && notify-send -u critical "Battery $percentage% full. Please unplug your AC adapter" && 
    mpv /home/mPC/Music/battery/batteryfull.mp3
   
    sleep 300
done


```

---

### Post by TheFu on 2022-11-29
Make up a log file and post a message to it when you see "full".  I'm confused.  Is that hard?

I have a script that checks my internet connectivity ever few minutes and logs when it works and when it doesn't work to a file, /var/log/internet-up.log.  There's a logrotate setup to ... er ... rotate the logs every week and compress them.  This makes calling the ISP to get refunds each month of major outages easy.
```
/root/bin/internet-up-summary.sh 
  Using /var/log/internet-up.log ... 
 Period 20221127-062611  - 20221129-151611
  Total Time: 3412 (min) 56.87 (hrs)
  Percent Up Time: 99.71 % 
  Percent Down Time: 0.29 % 
  Total Down Time: 10 min or 0.17 hrs
 Currently: UP

```
A few weeks ago, they caused a 2+ hour outage:
```
$ /root/bin/internet-up-summary.sh /var/log/internet-up.log.2.gz
  Using /tmp/internet-up.log.2
 ... 
 Period 20221113-062611  - 20221121-062411
  Total Time: 11520 (min) 192.00 (hrs)
  Percent Up Time: 98.68 % 
  Percent Down Time: 1.32 % 
  Total Down Time: 152 min or 2.53 hrs
 Currently: UP

```
Logs are good.
There's a way to sent messages to syslog too. I just don't do that.

---

### Post by meetdilip on 2022-11-29
Thanks. Used Python, and logging was easy. I guess it is working now. Will try to share it after testing.

---

### Post by meetdilip on 2022-12-01
I am using **psutil** in Python with a **while True:**

Wondering whether there is any option to use something like
[B]
while(status = battery.power_plugged): [/B]

instead of [B]while True:

[/B]I mean, run the logging part of the code only if the battery is plugged in

Thanks.

---

### Post by Claus7 on 2022-12-02
Hello,

I do not get exactly the: 
> **meetdilip said:**
> Is there a default battery charge log available in 22.04? Does it show when the charge was 100% the last time?

Thanks.

In order to keep an eye on your battery you could search for Power Statistics under Applications (or search for it). When opened you could go to Laptop battery->History and from there having the options Charge (for Graph type) and 1 week (for Data length) these will show you what you are looking for.

Regards!

---

### Post by meetdilip on 2022-12-03
Thanks, had no idea GUI exits. 

I am using a Python script that I wrote which creates a log entry every time the battery is full. I am able to run it with a while loop set to condition True so that it run infinitely. Instead, I want the testing code to be run only when " **battery.power_plugged " **condition is True. Not sure how to set that in Python.

---

### Post by meetdilip on 2022-12-03
Got it fixed. :)

---

