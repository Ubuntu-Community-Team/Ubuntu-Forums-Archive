---
title: "Trying to setup cron job to sync my time"
date: 2007-05-02
forum: General Help
---

### Post by Ould on 2007-05-02
Hi everyone,

I have been trying to setup a cron job on my edgy mythtv box for some time with little luck. I am here hoping someone may be able to help me out. 

The first thing I tried was to run "crontab -e" and then entered in my parameters following a how to. Basically trying to run "ntpdate pool.ntp.org"(can't remember if that is the right url but something like that). This didn't seem to work at all and I had to keep updating the time manually as it goes out of sync on a pretty regular basis. 

Next I read some more about cron jobs not ever really using them before and found that I could put a script into the folder /etc/cron.hourly and it would run it hourly. This seemed like a better way to do things so I went ahead and whipped up a quick script as follows:

#!/bin/bash

clock=clock.psu.edu

/usr/sbin/ntpdate -u $clock >& /home/kevin/setclock.log  #so I can see if it works

I did a chmod +x on the file and named it simply setclock.cron. If I run it manually in the terminal as:

sudo /etc/cron.hourly/setclock.cron

it works as expected and updates the log file. So I thought I was golden and left it for a couple days, went to check today and the last time it ran was when I ran it manually. I have checked and it appears that cron is running:

ps aux | grep cron
root         4650  0.0  0.0       2200    580 ?                  Ss      Apr19   0:00  /usr/sbin/cron

I am at a loss of what else I can check here? Really I only need this to run daily but I put it in hourly so I could see if it was working or not.

Any help would be appreciated, I am open to suggestions. System is Ubuntu Edgy, with MythTV and OpenBox if it makes a difference.

Thanks,

Kevin

---

### Post by dannyboy79 on 2007-05-02
> **Ould said:**
> Hi everyone,

I have been trying to setup a cron job on my edgy mythtv box for some time with little luck. I am here hoping someone may be able to help me out. 

The first thing I tried was to run "crontab -e" and then entered in my parameters following a how to. Basically trying to run "ntpdate pool.ntp.org"(can't remember if that is the right url but something like that). This didn't seem to work at all and I had to keep updating the time manually as it goes out of sync on a pretty regular basis. 

Next I read some more about cron jobs not ever really using them before and found that I could put a script into the folder /etc/cron.hourly and it would run it hourly. This seemed like a better way to do things so I went ahead and whipped up a quick script as follows:

#!/bin/bash

clock=clock.psu.edu

/usr/sbin/ntpdate -u $clock >& /home/kevin/setclock.log  #so I can see if it works

I did a chmod +x on the file and named it simply setclock.cron. If I run it manually in the terminal as:

sudo /etc/cron.hourly/setclock.cron

it works as expected and updates the log file. So I thought I was golden and left it for a couple days, went to check today and the last time it ran was when I ran it manually. I have checked and it appears that cron is running:

ps aux | grep cron
root         4650  0.0  0.0       2200    580 ?                  Ss      Apr19   0:00  /usr/sbin/cron

I am at a loss of what else I can check here? Really I only need this to run daily but I put it in hourly so I could see if it was working or not.

Any help would be appreciated, I am open to suggestions. System is Ubuntu Edgy, with MythTV and OpenBox if it makes a difference.

Thanks,

Kevin

well, all I did was first

sudo -i

(enter sudo password)

this will basically give you a root prompt.

crontab -e

then within that file,  add this

#ntp server sync
@hourly /etc/network/if-up.d/ntpdate

and then save the file by hitting ctrl X, then hit "Y", then hit "Y" again and then

exit

to get back to your username prompt. that's it. mine stays right on the money. then if you want to make sure it's working, simply take a gander at /var/log/syslog file using this command

sudo cat /var/log/syslog | tail

---

### Post by Turellius on 2007-05-02
It goes out of sync on a regular basis...check your motherboard battery.  Often times if a clock keeps losing time, it's due to a failing CMOS battery.

---

### Post by dannyboy79 on 2007-05-02
good call, i completely forgot about that.

---

### Post by Ould on 2007-05-02
Thanks for the replies guys. The crontab method is the first method I used and it didn't seem to work at all. And when I said going out of sync, it's not bad but it may go out 2-3 mins over the course of a couple days but that is enough to mess up the beginning and end of my recordings in MythTV. 

It almost seems as though cron just isn't working correctly but it appears as though it is running correctly but it just doesn't run the jobs. I will try the crontab method again now and see if it will work.

Kevin

---

### Post by dannyboy79 on 2007-05-02
please show me the output from syslog, it'll show whether or not your cron jobs are running.

---

### Post by gizmo2007 on 2007-05-02
Hello,

Try going to /etc/crontab and opening it in an editor.  This file needs to have entries in it to run the hourly, daily, weekly ect. cron files.  They will look something like

1 * * * *  root run-parts /etc/cron.hourly
ect.

If it still does not work try entering your cron directly into the crontab file (must be root to save).

20 4 * * *  root (command) 

*'s are minute, hour, day, month, day of the week , then  user , then command

Hope this helps, I have been running Mandriva for years, Still new to Ubuntu though....

---

### Post by rich.bradshaw on 2007-05-02
just use the ntp server, does it automatically.

---

### Post by gizmo2007 on 2007-05-02
That would be a simpler and less timely approach

---

### Post by Ould on 2007-05-02
Thanks everyone, I got it working finally. I read through the syslog as suggested and saw that the cron.hourly was trying to run but it wasn't picking up my script I had made. Apparently it didn't like the fact that it had an extension on the file(I used .cron so I would know what it was for). Anyways I removed that and let it run again an hour later and it appears that it is working now. :-D

Thanks again!!

Kevin

---

### Post by dannyboy79 on 2007-05-03
glad to be of help!

---

