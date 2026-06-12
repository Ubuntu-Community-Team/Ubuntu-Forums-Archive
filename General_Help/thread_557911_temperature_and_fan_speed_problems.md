---
title: "temperature and fan speed problems"
date: 2007-09-23
forum: General Help
---

### Post by DaveRowell on 2007-09-23
The system logs (kern log, messages and syslog) are filled with messages like this - "Jul 22 10:32:15 CompaqSR1265 kernel: [ 3187.805039] ACPI: Unable to turn cooling device [c18b5dec] 'on'"  A new message seems to show up every 6 seconds or so.  Running the Gnome sensors applet I see reasonable temperatures and fan speeds - CPU usually runs 50 to 60 C - fan just less than 1000 rpm.  

Am I right is sensing that there is no "real" problem here?  How do I get 'whatever' to run properly so I don't get these messages?  How can I get the CPU to run a little cooler?

Hardware: Compaq Presario SR1265, AMD Athlon XP 3200+ processor, VIA S3G Unichrome IGP video, 1 Gb RAM, 160 Gb ATA hard drive, Lite-On SOHW-1693 DVD R/W, Samsung SW252S CD R/W, 17" Compaq FP7317 monitor, RoadRunner supplied Terayon TJ716 cable modem on ethernet - dual boot Win XP & Ubuntu Linux - no local network

---

### Post by fjgaude on 2007-09-23
I'm running 7.04 and my system logs show fan on and cpu temp as 40C. Never changes, this temp so I know the monitoring isn't correct.

Have you tried upgrading to Feisty? Many improvements in how the BIOS is handled.

---

### Post by DaveRowell on 2007-09-23
I AM running Feisty - 7.04
Should have said so in the first place - sorry.

---

### Post by caen1944 on 2007-09-23
fjgaude,

My temps were always 40 too. I managed to fix this, and I remember it being pretty complicated. I'm not on that system right now, but when I get to it I'll try to figure out what it was I did. 

I remember having to install some sort of monitor package, than had to run some type of probe from the command line, and paste the results into a configuration file. As it is now, I get all sorts of info about the system, although the CPU and MB temps are mixed up, I at least know what they are. If I can figure what package I installed, the instructions were in the documentation.

Send me a message if I havn't looked this up in a day or so. 

caen

---

### Post by caen1944 on 2007-09-23
I think it was lm-sensors. Try this link:
[http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors](http://www.quietearth.us/articles/2006/09/30/Ubuntu-Sensor-temperature-monitoring-with-lmsensors)

---

### Post by DaveRowell on 2007-09-23
I have lmsensors installed and running - that's how I "know" that my fan speed and CPU temp are within reason.  But something fundimental is writing this error to the log files every 6 seconds even tho everything seems to be OK.  I need to know how to fix whetever is writing the error message.

Thanks for thinking about my problem - I appreciate it.

---

### Post by cdmwebs on 2007-09-25
Same box, same exact problem.  Feisty, Gutsy, Debian Etch all do the same thing - dump the ACPI unable to turn cooling device on message every six seconds or so.  I once found a "solution" that dumped the messages to /dev/null, but I'd like to find a fix too!

---

### Post by cdmwebs on 2007-10-06
Problem solved!!

Found it here: [http://www.centos.org/modules/newbb/viewtopic.php?topic_id=8158]("http://www.centos.org/modules/newbb/viewtopic.php?topic_id=8158")!

The line in bold is what fixes mine.

```

Check your temperature threshold
# cat /proc/acpi/thermal_zone/THRM/trip_points

My original threshold was relatively low, critical (s5) at 60C, active[0] set to 50C, which cause my system to shut down a few time under heavy load.
Under normal usage my system running around 52-55C and ~60C under heavy load

I set to higher/proper threshold and the spam went away:
**# echo -n "65:60:50:55:50:45" > /proc/acpi/thermal_zone/THRM/trip_points**

Although the underlaying problem is still there, I don't expect to see it unless my system has trouble keeping it self cool.
Most of review I saw out there for Shuttle X100/X200 (core duo) runs around 52-62C under normal usage, so I am good for now.

I guess I can turn the acpi off, but I don't want my system to overheat and melt down.

```

Works for me.  Apparently, the trip points for my system were set for ridicously negative temperatures.  Something like -215C...

---

### Post by DaveRowell on 2007-10-23
OK starting to follow your procedure I get this:

david@CompaqSR1265:~$ sudo cat /proc/acpi/thermal_zone/THRM/trip_points
Password:
critical (S5):           100 C
passive:                 -248 C: tc1=4 tc2=3 tsp=60 devices=0xc18b5338 
active[0]:               -266 C: devices=0xc18b5dec 

It looks like these are all off base doesn't it?

Forgive my ignorance but will mimicking your next step (echo...) hurt anything?  If it does, how might I recover?

---

### Post by drpaul on 2007-10-23
I queried my system and found

 cat /proc/acpi/thermal_zone/THR1/trip_points 
critical (S5):           95 C
passive:                 88 C: tc1=2 tc2=3 tsp=50 devices=0xdffe75f4 

these temps seem quite high; my fan seems to come on and off in the 39-45 C range.

These settings and behavior don't seem consistent. anyone shed some light on this for me?

Paul

---

### Post by krazykral on 2008-02-26
Hi Im sorry if this thread is closed 

but my friend just recently installed gutsy on his aspire 5100 
and got the same problem as drpaul.

with the temp probe and such

the error was something along the lines
[critical temperature reached (95C) shutting system down]

but the temp given and actual temp were obviously different

when he checked the cmos the temp wouldnt shouw up like it normally does

now he cannot boot or install any OS
now his computer is bricked

please if anyone could shed some light on how to fix this problem preferrably through software manipulation(firmware and such) rather than hardware but if to replace the temp probe is the only option I think he we might be screwed would
Please help as soon as posbile

krazykral

---

### Post by Yellow Pasque on 2008-02-26
Have you tried clearing the CMOS? There's probably a jumper to do that and it's something free/easy to try before giving up on the system as "bricked"

---

