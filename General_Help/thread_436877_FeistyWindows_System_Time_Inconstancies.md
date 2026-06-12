---
title: "Feisty/Windows System Time Inconstancies"
date: 2007-05-08
forum: General Help
---

### Post by mattmcmanus on 2007-05-08
I'm having this weird issue with my system time. I hope I can explain it accurately.

My time is always right within feisty. But when I restart my machine to go into windows my time in windows is always 4 hours fast. I can change it or leave it fast and when I reboot back into ubuntu the time is fine. If I reboot after being in feisty and go straight into the bios, the time is 4 hours fast. I could simply restart my machine just to go straight back into feisty and the bios will be 4 hours fast but I wont have to change the time when the OS is loaded cause it will be back. 

Both are set to the right timezones and i've turned time synchronization off on both so the only thing changing the clock is me. 

Has anyone had this problem? It just seems so strange to me.

---

### Post by ohgod on 2007-05-08
When you installed Ubuntu, how did you answer the question about your system clock?  The choices are either that your system clock is set to UTC, or to local time.  I'd guess this has something to do with it.

---

### Post by mattmcmanus on 2007-05-08
Honestly, I do not remember.Whatever the default answer was I would guess. 

I can see your point with that though, but it still doesnt make sense cause my timezone is EST (-5). So if the time was 5 hours fast then that could point to that, but its not, its only 4 which is why im so confused.

---

### Post by z0phi3l on 2007-05-08
> **mattmcmanus said:**
> Honestly, I do not remember.Whatever the default answer was I would guess. 

I can see your point with that though, but it still doesnt make sense cause my timezone is EST (-5). So if the time was 5 hours fast then that could point to that, but its not, its only 4 which is why im so confused.

Factor in Daylight Savings and it's -4 for some reason :/

---

### Post by hanzomon4 on 2007-05-08
Set ubuntu and windows to local time, or try utc time. I had the same problem with ubuntu and sabayon.

---

### Post by kebes on 2007-05-08
Yes this is a common dual-booting issue. Basically, Windows thinks that the hardware clock is set to local time, whereas Linux by default assumes the hardware clock represents UTC (and makes the timezone adjustment itself). If you are comfortable with the commandline, you can fix this in Linux by doing something like:

1. Set date to current time, if required (instead of "11:02" use the current time):
$ sudo date -s 11:02
2. Update the hardware clock with the newly updated time:
$ sudo /sbin/hwclock --systohc --localtime
3. Check that the change took effect:
$ /sbin/hwclock --localtime
Tue 08 May 2007 11:01:41 AM EDT  -0.641764 seconds
4. Load the hardware clock time back into the system:
$ /sbin/hwclock --hctosys --localtime

The above procedure will (if memory serves correctly) set Linux to be running from the hardware clock as local time. Then when you boot into Windows, the time should look right.


If you don't want to use the commandline, go to where you edit the time, in Linux, and find the option that controls whether the hardware clock is "local time" or "UTC" (may be marked as "GMT"). Again, change Linux to use "local time" and then make sure the clock is updated. Then reboot into Windows.

Hope that helps.

---

### Post by hanzomon4 on 2007-05-08
> **kebes said:**
> 
If you don't want to use the commandline, go to where you edit the time, in Linux, and find the option that controls whether the hardware clock is "local time" or "UTC" (may be marked as "GMT"). Again, change Linux to use "local time" and then make sure the clock is updated. Then reboot into Windows.

Hope that helps.

In other words right click on the clock in linux and select preferences. Then untick "use utc"

---

### Post by mattmcmanus on 2007-05-09
Hey Kebes, Thanks for the help. 

Unfortunately, this still doesnt help. My time is NOT set to use UTC and when I run those commands, everything runs fine (no errors) but when I reboot my clock is till 4 hours ahead. I also tried running those commands with UTC on and still, nothing actually changes. 

When I set the time on UTC my linux clock jumps ahead four hours but when I adjust the time, it says that is is the right time, and if I change it it doesnt actually show.

---

### Post by hanzomon4 on 2007-05-09
Thats because you can only change UTC time in the BIOS, the adjustment only effects local time. Set both linux and windows to local time, adjust, and reboot.

---

### Post by mattmcmanus on 2007-05-09
> **hanzomon4 said:**
> Thats because you can only change UTC time in the BIOS, the adjustment only effects local time. Set both linux and windows to local time, adjust, and reboot.

UTC was off originally and I still had the problem. It is off now. My Clock says 8:25. If i reboot and go into the bio my clock will say 12:25. If I change it back to 8:25 in the bios and the boot into ubuntu the clock will still read 8:25 like it did before.

---

### Post by seamuso on 2007-05-09
I was having the same problem .. try [ [COLOR="Red"]this[/COLOR]](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Troubleshooting#How_to_disable_system_time.2Fdate_from_being_reset_to_UTC_.28GMT.29)

---

### Post by mattmcmanus on 2007-05-09
This looks promising. I will give this a try when I get home from work.

---

