---
title: "Time problems on dual-boot system"
date: 2008-05-23
forum: General Help
---

### Post by allaboutsam on 2008-05-23
I'm having major time problems on a dual-boot system.

Both Ubuntu and Windows are set to use local time, and Windows is set to ignore daylight savings. But if it's right in Windows (say, 1:00 am), it's wrong in Ubuntu (9:00am the previous day), and vice versa. I've tried setting both to UTC with similar results.

The effect is as follows: I log onto Windows and notice that the time is wrong. I reset it to be correct, make sure that the "automatically adjust time for daylight savings" box is unchecked, and check the registry to make sure that the RealTimeIsUniversal key is unset. All looks well. I log off Windows and onto Ubuntu, where again I notice that the time is wrong. I reset it to be right, and make sure that UTC=no in /etc/default/rcS. I log off of Ubuntu and back onto Windows, and the time is wrong again. Etc. etc.

I don't think it's the clock battery, as the minutes and seconds remain correct--it's just the hours that change. And I've Googled around and searched the forums here for other suggestions, but found only the standard advice about the abovementioned registry key and the rcS file. Anyone have any idea what is going on?

In case it matters, I'm running Windows XP SP2 and Ubuntu 8.04 on a Dell Latitude D400. Also, note that the two systems are on different hard drives that I swap in and out of the computer.

Many thanks,
allaboutsam

---

### Post by Steve413z on 2008-05-23
if UTC is set to no, try setting it to yes

---

### Post by allaboutsam on 2008-05-23
Many thanks, Steve.

Three more tries and it's working, though UTC is still set to "no." No clue what I did this time to make it work, but as it's okay I'm going to leave it alone.

---

### Post by Steve413z on 2008-05-23
the other thing is, make sure you have the same time zone set in both windows and ubuntu, and automatically change daylight savings should be ON on both OS'es (unless you live in Arizona, or another place that doesn't follow DST), and if both OS'es are set to use UTC, it's probably better

---

### Post by Steve413z on 2008-05-23
you SHOULD set UTC to YES, on both windows and linux because if you both windows and linux thinks its the beginning of daylight savings time, they will both add 1 hour to your system clock, for a total of 2 hours, however if you set it to UTC, the system clock never actually changes, because it's set to UTC, but the operating system compensates, by subtracing the correct number of hours from UTC

for example in _eastern time zone_:
you subtract 4 hours from UTC during daylight savings (summer) 
you subtract 5 hours from UTC during standard time (winter)



so right now it's 5:45 UTC
minus 4 hours for eastern daylight time
you get 1:45

<rant>I hate daylight savings time, I once missed a test worth 10% of my final grade for a class, because I was waiting for the class to start in another room, and I was relying on the schools clock that had not been set for more than 2 weeks past the day it was supposed to be changed, I walked to class thinking I was 10 minutes early, only to discover, I was 50 minutes late </rant>

---

