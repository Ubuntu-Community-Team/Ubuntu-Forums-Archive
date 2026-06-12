---
title: "Script in /etc/pm/sleep.d not working"
date: 2016-10-23
forum: General Help
---

### Post by ultragamer2 on 2016-10-23
I have a script that enables the pc to wake up automatically from tv schedule data.

File path/name is /etc/pm/sleep.d/95_timer.sh

**Anyway It works properly** but only if I double click on it and choose 'Run in Terminal'.  It does not work if I choose run, or automatically when you put the pc in suspend mode.

It's probably something simple like chmod or visudo, I tried those but I might have made a mistake, I'm a newbie.



Here is the script from
[https://tvheadend.org/projects/tvheadend/wiki/Wakeup](https://tvheadend.org/projects/tvheadend/wiki/Wakeup)


```
#!/bin/bash
#
# set ACPI Wakeup alarm
# safe_margin - minutes to start up system before the earliest timer
# script does not check if recording is in progress
#
#

echo 1 > /timer

# bootup system 60 sec. before timer
safe_margin=120

# modyfy if different location for tvheadend dvr/log path
cd ~hts/.hts/tvheadend/dvr/log

######################

start_date=0
stop_date=0

current_date=`date +%s`

for i in $( ls ); do
tmp_start=`cat $i | grep '"start":' | cut -f 2 -d " " | cut -f 1 -d ","`
tmp_stop=`cat $i | grep '"stop":' | cut -f 2 -d " " | cut -f 1 -d ","`

# check for outdated timer
if [ $((tmp_stop)) -gt $((current_date)) -a $((tmp_start)) -gt $((current_date)) ]; then

# take lower value (tmp_start or start_date)
if [ $((start_date)) -eq 0 -o $((tmp_start)) -lt $((start_date)) ]; then
start_date=$tmp_start
stop_date=$tmp_stop
fi
fi
done

wake_date=$((start_date-safe_margin))

echo $start_date >> /timer
echo $wake_date >> /timer

# set up waleup alarm
if [ $((start_date)) -ne 0 ]; then
echo 2 >> /timer
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo $wake_date > /sys/class/rtc/rtc0/wakealarm
fi
```

---

### Post by ultragamer2 on 2016-10-24
Ok I found the answer with new Ubuntu versions it has to be in
[h=2]/lib/systemd/system-sleep/[/h]

---

### Post by ajgreeny on 2016-10-24
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by Keith_Helms on 2016-10-24
Does that mean that the /etc/pm subdirectories are no longer used with systemd?

---

