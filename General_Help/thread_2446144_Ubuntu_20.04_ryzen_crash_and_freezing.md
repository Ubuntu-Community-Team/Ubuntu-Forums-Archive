---
title: "Ubuntu 20.04 ryzen crash and freezing"
date: 2020-06-25
forum: General Help
---

### Post by benomas on 2020-06-25
Hi, it is my first time posting here.

I am stuck triying to solve a problem my self, so I come here asking for some advices.

In november I get a new ring, changing from intel to amd, (I already use ubuntu with a ryzen 2600 with no problems), 
the change consist on a rzen 3600, a gigabyte x570 ud motherboard and 4x8 3600 corsair vengance memory.

From november until now, i am having random crashes or freezings while i am programing (i am web depeloper) ,I am having a lot of work and just ignore this issu, but now I'm going crazy.

I search for solutions in google but there is not just "same case" - "one solution", what I found is people saying incompatibility issus with ryzen 3 gen procesors, problems with mother board, problems with ram, problems with network adaptart and etc etc, nothing that really helps me.

I test a lot of situations and hardware

-Problem is not present in windows 10
-Mem test passed for 5 hours without errors
-Prime95 torture test on ryzen runs for hours in windows 10 with no problems
-Reinstall ubuntu (sometimes the error happends when i am installing :/ )
-Remove all usb hardware (the error continues)
-Adjust some params in bios (turn off ryzen turbo bost and other things) 
-Replace motherboard (the problem persist)
-Replace memory (the problem persist)
-Trying new ubuntu instalacion from 2 distics ssd and a old hard drive (the problem persist)
-Add a new cooler thinking the problem was temperatures (the problem persist)
-Replace vidcards, i already use 6 different nvidia and amd (the problem persist)
-Replace wifi usb card, (the problem persis).

So now i am here with no more ideas for test and with **the problem persist**.

All the time I was trying to catch some pattern from logs, but 90% of the time i get thigs like the attached pics (syslog and kern.log)

I hope someone here can give me some tips about what more can i try (I am now sad resigned to maybe go back to develop in windows, because aparently my hardware cant work well with ubuntu).

thanks for watch my post and sorry for my bad english :(

[ATTACH=CONFIG]286311[/ATTACH][ATTACH=CONFIG]286312[/ATTACH]

---

### Post by TheFu on 2020-06-25
We prefer text over images here. Please. There's always a way to get the text so images just aren't necessary. When posting logs, commands, etc, please use "code tags" to make things readable.

PSU and RAM timing are where I'd start. Simplify the system to 1 simple GPU (AMD is probably best), the RAM, the CPU and wired ethernet. Only connect a keyboard and mouse for the USB. NOTHING ELSE. No USB storage. Definitely NO wifi.  Run that way for a week.  Be certain to change the log retention (journald.conf) so a few boots are retained and you can capture those logs. After a crash, review the boot and syslog data for what happened just before. Look for any errors and warnings.

My Ryzen 2600 needed some tweaks for the 3200 RAM a few years ago.  BIOS updates helped but not quite enough before I adjusted the timings and voltage to the RAM. My RAM wasn't on the approved list, but it was G.Skill (a reputable, but less expensive brand).

Our systems have temperature sensors, so we don't need to guess about overheating anymore.

And to prevent too much data loss, I'd get hourly snapshots working so you never lose more than an hour of work. LVM, ZFS, and some backup tools can do that.

Text, not images, please.

---

