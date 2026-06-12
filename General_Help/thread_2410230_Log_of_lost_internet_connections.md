---
title: "Log of lost internet connections"
date: 2019-01-12
forum: General Help
---

### Post by raleigh3 on 2019-01-12
I am having a big problem with lost internet connections with my DSL.

I would like to create a log to be able to show the technician when he comes next week.

I would like for it to only log pings that generate 100% packet loss. Thanks..

This script generates all ping attempts including successful ones.

```
while true; do

date >> Internet_Connection_Log.txt
echo >> Internet_Connection_Log.txt
ping  47.182.239.232 -c 1 >> Internet_Connection_Log.txt
echo >> Internet_Connection_Log.txt
sleep 180
done
```

---

### Post by TheFu on 2019-01-12
I ping 1 time every other minute and put all attempts into a log. Logrotate keeps the log files small.  Wrote a script to count the failed ping attempts. Here's the output:
```
$ internet-up-summary.sh 
  Using /var/log/internet-up.log ... 
 Period 20190106-062611  - 20190112-185011
  Total Time: 9238 (min) 153.97 (hrs)
  Percent Up Time: 99.44 % 
  Percent Down Time: 0.56 % 
  Total Down Time: 52 min or 0.87 hrs
 Currently: UP
```
By having the full logs, I can prove both that the machine was on and working AND that the IPs I ping were unavailable.  I use extremely well-know IPs.

The summary script know how to gunzip older logs to show a report for those too.
```
$ internet-up-summary.sh /var/log/internet-up.log.20.gz 
  Using /var/log/internet-up.log.20.gz ... 
  Using /tmp/internet-up.log.20
 ... 
 Period 20180812-062612  - 20180819-062411
  Total Time: 10080 (min) 168.00 (hrs)
  Percent Up Time: 99.07 % 
  Percent Down Time: 0.93 % 
  Total Down Time: 94 min or 1.57 hrs
 Currently: UP
  Removing /tmp/internet-up.log.20

```
The perl script for the summary is about 70 lines - here [http://*******.us/DQgEKW](http://*******.us/DQgEKW) .  The ping script is 4 lines.   [http://*******.us/0xSraQ](http://*******.us/0xSraQ)

Hope this is helpful.

ARG!!!! ******* is blocked? Just put that into the ****** parts to get the scripts.

---

### Post by raleigh3 on 2019-01-12
Thanks.

---

### Post by TheFu on 2019-01-12
> **raleigh3 said:**
> Thanks.

s-p-r-u-n-g-e
is the missing URL part, just remove the dashes.  It shouldn't be this hard.

---

### Post by raleigh3 on 2019-01-12
Ok.

Found a little easier method.

```
while : ; do
     if ! ping  -c 1 47.182.239.232 ; then
          printf "\n%s\n" "ping failed at $(date)" >> /home/andy/bin/Internet_Connection_FAILURES_Log.txt
          cvlc --play-and-exit /usr/share/sounds/My_Sounds/Alarm-sound-buzzer.mp3
     fi
     sleep 60
done
```

---

### Post by TheFu on 2019-01-13
If you leave you system on 24/7, having it make noise in the middle of the night isn't ideal.
Also, if there is an outage and I don't notice, does it really matter?  I've been working for multiple hours when the internet was out and didn't notice.  Much of my work happens on local servers, so the internet isn't important much of the time.

But I can see where having a noise when the tech is visiting would be effective.

---

