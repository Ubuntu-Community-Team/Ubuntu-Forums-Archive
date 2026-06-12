---
title: "Overheating problem, need help as soon as possible!"
date: 2006-07-10
forum: General Help
---

### Post by Aven on 2006-07-10
Hello, I've been recently having a big problem.

Eveytime I watch a video, my computer immediatly shuts down (with no warning) . Then I wait for about 5 minutes because it doesn't turn on at all; then after it's turned on, it says the computer was shutdown for a "thermal event (overheating)"  and says "Service your unit to resolve this problem" what's that mean? 

Is there a way to have ubuntu give me a warning or not even do anything when the computer is overheating? because the fans are working great and I don't know that's causing this. I've cleaned out the fan as well, still having a problem. I have a 512MB RAM machine.

I've also done the following things:

```
sudo /etc/init.d/acpid
```
That didn't solve it.

```
killall gnome-power-manager
```
I basiclly shut down gnome-power-manager and still having issues.

Any idea how I can stop ubuntu from shutting down my computer when it overheats?

---

### Post by Anduu on 2006-07-10
Check your BIOS or get lmsensors installed so you can see what kind of temps you are running [http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors)

I would then check to see what temps are safe for your CPU 

These charts are for AMD CPUs
[http://www.thedigerati.us/info/amdcpuchart.html](http://www.thedigerati.us/info/amdcpuchart.html)

These have Intel chips listed
[http://www.technibble.com/what-is-my-computers-maximum-cpu-temperature/](http://www.technibble.com/what-is-my-computers-maximum-cpu-temperature/)

If your temps fall within the "safe" ranges you could go into your BIOS and adjust the auto shutdown temp.

---

### Post by DR_K13 on 2006-07-10
> **Anduu said:**
> Get lmsensors installed so you can see what kind of temps you are running [http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lmsensors)

I would then check to see what temps are safe for your CPU 

These charts are for AMD CPUs
[http://www.thedigerati.us/info/amdcpuchart.html](http://www.thedigerati.us/info/amdcpuchart.html)

These have Intel chips listed
[http://www.technibble.com/what-is-my-computers-maximum-cpu-temperature/](http://www.technibble.com/what-is-my-computers-maximum-cpu-temperature/)


I didnt know a Thunderbird could handle 95c :shock:  No wonder I never had to turn on the heater in winter time 
when I had my Tbird cluster./

---

### Post by Aven on 2006-07-10
Hi, I tried working sensors but won't work. Would I have to reboot the computer for it to detect the sensors? right now it's saying "sensors not found!"

---

### Post by Anduu on 2006-07-10
> **Aven said:**
> Hi, I tried working sensors but won't work. Would I have to reboot the computer for it to detect the sensors? right now it's saying "sensors not found!"

lmsensors can be tricky to set up...follow the how to very closely and you should get them to work.

Just out of curiosity what kind of CPU do you have and what is the emergency shutdown temp set at in your BIOS?

---

### Post by Aven on 2006-07-10
Ah, I had to reboot.
Sensors:
```
adm1027-i2c-2-2e
Adapter: SMBus I801 adapter at e000
V1.5:      +1.488 V  (min =  +1.42 V, max =  +1.58 V)
VCore:     +1.210 V  (min =  +1.21 V, max =  +1.34 V)   ALARM
V3.3:      +3.300 V  (min =  +3.13 V, max =  +3.47 V)
V5:       +5.013 V  (min =  +4.74 V, max =  +5.26 V)
V12:      +11.469 V  (min = +11.38 V, max = +12.62 V)   ALARM
CPU_Fan:   4215 RPM  (min = 4000 RPM)
fan2:         0 RPM  (min =    0 RPM)
fan3:         0 RPM  (min =    0 RPM)
fan4:      3351 RPM  (min =    0 RPM)
CPU:      +109.25°C  (low  =   +10°C, high =   +50°C)     ALARM
Board:    +62.25°C  (low  =   +10°C, high =   +35°C)     ALARM
Remote:   +78.75°C  (low  =   +10°C, high =   +35°C)     ALARM
CPU_PWM:   255
Fan2_PWM:  255
Fan3_PWM:  255
vid:      +1.275 V  (VRM Version 9.1)
```

> **Anduu said:**
> lmsensors can be tricky to set up...follow the how to very closely and you should get them to work.

Just out of curiosity what kind of CPU do you have and what is the emergency shutdown temp set at in your BIOS?
How do I find out? I don't really know what that is =\

---

### Post by Anduu on 2006-07-10
Well if those numbers are correct you have some serious heat issues....

CPU:      +109.25°C  (low  =   +10°C, high =   +50°C)     ALARM

This is not good....

I dunno tho...from everything I have heard you computer shouldn't function at all at temps like that :-k

CPU_Fan:   4215 RPM  (min = 4000 RPM)

Your CPU fan seems to be running a little slow...mine runs at 5000 rpm....

---

### Post by Aven on 2006-07-10
Oh I see. Any idea how to clean the inside of a fan? I think that's the problem.

---

### Post by Anduu on 2006-07-10
Just remove the fan and blow the dust out..also clean any dust from your case fan and vents.

I doubt that the fan running only 4000 rpm would cause that big of a temperature difference...

I am still suspect of that 100+ degrees C temperatue.Check you BIOS and see what temps it is reading.

---

### Post by ekarni on 2006-07-10
Your processor is (supposedly) hot enough to boil water on!  I agree, those numbers sound very high.  One possibility is that the calibration is off for lmsensors; I know my CPU reads below room temperature during the winter (hah!).

However, your problem does sound like it could be caused by overheating.  As previously suggested, open the case, blow out any dust, and check that all fans are operating.

To determine your CPU type, type *sudo lshw* at the command line.  Processor info will be near the top.

---

### Post by nanotube on 2006-07-11
it's not just the fan (the fan itself is unlikely to have dust buildup, since it spins around all the time), but the heatsink. make sure to take a can of compressed air to the heatsink fins and blow that out.

also, it may be that the heatsink for whatever reason is not in good contact with the cpu. take the whole heatsink+fan assembly off the cpu, clean off the old thermal paste (if you don't find any, well, that there was your problem :) ), put a nice dab of fresh thermal paste on it, and reinstall the heatsink. (you can find guides online for proper paste application, etc).

---

### Post by insane_alien on 2006-07-11
or you could get a better fan/heatsink combo. i had to get one after my P4 kept reading >80*C with the stock. now it only reaches 50*C if its under a heavy load :)

---

### Post by Aven on 2006-07-11
Yeah, well the fan is running smoothly from what I can see, I cleaned out the dust from the outside and also blew the inside. Heatsink was also cleaned up.

```
.Check you BIOS and see what temps it is reading.
```
How would I do that? :)

---

### Post by Ramses de Norre on 2006-07-11
When booting press a certain key stroke on the very first screen you see (the particular screen stroke is mentioned in that screen, something like "press <del> to enter setup") to enter setup and take a look around there, you can see the sensor readings somewhere but names in menus differ with different mobo's..

---

