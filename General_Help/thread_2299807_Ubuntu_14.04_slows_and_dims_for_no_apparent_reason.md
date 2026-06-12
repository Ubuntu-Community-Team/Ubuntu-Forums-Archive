---
title: "Ubuntu 14.04 slows and dims for no apparent reason"
date: 2015-10-21
forum: General Help
---

### Post by Lee_Nowell on 2015-10-21
Hi All,

I have Ubuntu 14.04 (64 bit) installed on a freshly installed laptop which are generally only really used for browsing the web and sometimes for doing the odd document/ spreadsheet etc. On initial boot, all seems to be fine however after a bit of use, both seem to get very slow and then have patches of say 10 or 20 seconds of unresponsiveness and the screen goes dim.  The frequency of these unresponsive patches seems to increase over time.  Reboot fixes the issue.

As most of the usage is browsing the web, I initially assumed it was a flash plugin issue based on some articles I found.  Firefox is installed by default but I have moved to Chrome (as suggested by one of the forums) and checked to ensure there is no flash plugin clash. The issue still exists.  Even disabling Flash plugin makes no difference.

I have run "top" whilst using the laptop and memory and CPU utilization seems fine.  Also, looking at /var/log I can't find anything of interest in any of the log files.

Further searching has drawn up a blank as to where next to go to try to find the source of the issue.

Anyone have any ideas how I can further debug this and understand the root of the problem?

thanks

Lee.

---

### Post by grahammechanical on 2015-10-21
You do not tell us the hardware specification of the machine. Please also include information about the video adapter and the amount of its own memory that it has.

Certain web sites have lots of active elements such as adverts that are in reality a form of video. These pages use a lot of system resources (CPU and RAM). I use Ubuntu Web Browser that cannot make use of Adobe Flash plugin and it is effected by these kind of pages in a detrimental way.

In Ubuntu when an application window goes grey it is because the application is busy. I get this in Libreoffice when I have 2 large documents open and both are being saved to disk. Things are not helped by the fact that the machine only has 1GB or RAM.

I also had this problem on one install of Ubuntu that was running out of disk space. 

Regards.

---

### Post by Dragonbite on 2015-10-21
Have you verified the power setting options and turn off the "dim" option if set?

I don't now if there is a power saver setting like Windows does, which scales back the CPU to save battery life.  I've heard mention of a "Powertop" application but don't know how to use it.

---

### Post by Lee_Nowell on 2015-10-22
The symptoms are as grahammechanical describes as the application being busy but it seems to have a wider effect.  e.g. If I have a browser open and then it starts behaving sluggishly then goes dim etc.  even doing things like starting a terminal with <ctrl><alt> T takes for ever... even executing "top" within the terminal seems to leave it thinking for ages before the info appears.  I am fairly sure it is not a memory issue, the machine very well spec'd for a simple install and browser running - 8gb ram, Core i5  and "top" has low memory and CPU usage anyway.

It is almost as if something is locking the CPU.   Any ideas how I can find out what?

thanks

Lee,.

---

### Post by Lee_Nowell on 2015-10-23
I did some more testing last night.  It does seem to be browser related and both Chrome and Firefox seem to exhibit the behavior.  Prior to these being run, it seems fine.  Any ideas what I can try to narrow down the issue?

thanks

Lee.

---

### Post by poorguy on 2015-10-23
i have experienced the same problem from time to time and sometimes it takes care of itself but in most cases i have to close the browser and then reopen the browser and it takes me right back to where i was and runs fine. there is an error message and i always send that in. next time this occurs i will try and save the message to post here.

i am on an old desktop box intel motherboard / intel core 2 duo e4300 / 4.0 gb ddr2 ram / ati 5450 graphics card / dual boot windows 7 / ubuntu 14.04 on two different hdd / default firefox web browser.
everything runs well most of the time this does happen every now and than.

---

