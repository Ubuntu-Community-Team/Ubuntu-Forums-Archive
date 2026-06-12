---
title: "Power safe policy for HDDs ?"
date: 2007-11-23
forum: General Help
---

### Post by VictorR on 2007-11-23
I'd like to install another HDD to my computer purely for backup purposes. As any hard drive is a pretty power consuming device I'd like to keep it inactive for most time, activating only once a day when backup data are going to be written to it.

Is it possible to set different power safe modes for two hard disks, say one is power off after 5 mins of inactivity, while another keeps turning? And how?

System -> Preferences -> Power Management GUI does not have such options at all.

Thanks in advance.

---

### Post by AllanP on 2007-11-23
What I did was buy an Acomdata hard drive enclosure. I have a few old IDE drives around and I popped a 160GB IDE drive into the enclosure. it has a USB connection (the more expensive have SATA connection as well). It is recognized immediately. Configure access to it and your off. This thing has a switch on it so you just turn it on when you need it.
Hope that helps.
They cost around $40.00

---

### Post by SnTholiday on 2007-11-23
AllanP has a good idea. 

I added a 250 GB HDD to an already existing 320 GB and have looked for those same settings in both Windows and Ubuntu. None exist that I can find to power off just one HDD. One other consideration you must think about when adding a second internal HDD is your existing power supply. Most power supplies that come with a PC are only 300-350 watts. Some video cards can take up to 150-200 watts by themselves, so I would think about upgrading your power supply unless you have already done so. What AllanP suggests may be a less
expensive alternative. I upgraded my power supply from the stock 300 watt to a 500 watt Master Cooler for
$60.00.

---

### Post by VictorR on 2007-11-24
Thanks, that's a good solution. I currently use Simple Backup, which scheduled to 2am, so I would prefer not to be personally involved in the process by mean of switching the drive on and off in the middle of the night :) Also If I were able to keep this drive inactive most of the time, the power consumption would be not a problem, as it supposes to be working when no other activities are expected (monitor is off) and this would be the cheapest (no extra cost for the enclosure) solution.

Any more ideas?

---

### Post by AllanP on 2007-11-24
It sounds like your requirements for backing up are more crucial than mine. With me it only takes a couple of minutes max to copy my personal data to the back up medium; my document stuff and my Thunderbird email profile.
Another thing I do is use Acronis True Image. I forget the cost; around $40.00 I think and I save an image of my permanent OS's maybe once a week. I do a lot of messing around installing software; playing with different distro's etc., so I'm inclined to mess things up periodically. It's just a hobby with me.
There's probably some wizards here that could write a script to mount and backup at a certain time onto a powered down drive; over my head though.

Regards, Allan

---

### Post by VictorR on 2007-11-26
Thank you, guys!
You gave me some new ideas to think about. As far as I could see I might use the following scenario:
1. an external drive in its USB enclosure with external power supply, unmounted, connected to the main power through the timer (I have a couple). X time is about 2:00 am.

The timer switches the enclosure on at about 1:30 am (the timer is not very accurate).
The script (or just a single command), activated by cron at 1:45 am, mounts the external drive.
Single Backup performs backing up data from 2:00 am to ... (should check how much it takes usually)
cron lazily unmounts the external drive say 15 mins later
the timer switches the drive off 15 mins after unmounting.
Done...

An enclosure costs $30, timer $5-8, the HDD cost depends on its specs.

---

### Post by AllanP on 2007-11-26
Sounds like a plan. Too bad you weren't local I could give you a drive lol.

---

### Post by VictorR on 2007-11-27
Thanks, 

Just for information - I have found this nice article about power saving in Linux 
[http://www.ma.utexas.edu/users/stirling/computergeek/powersaving.html]("http://www.ma.utexas.edu/users/stirling/computergeek/powersaving.html")

I have already got two disks in my PC indeed - one is Ubuntu and another - Windows 2000 (dual boot and virtual OS), but actually have not booted Windows for long. Now I am thinking about moving useful data from Windows disk to Ubuntu. This would give me enough room for backup on Win disk, and could allow also to put this disk to unmounted sleeping state for most time.

---

