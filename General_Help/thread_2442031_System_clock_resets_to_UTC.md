---
title: "System clock resets to UTC"
date: 2020-04-28
forum: General Help
---

### Post by lwalper on 2020-04-28
Can anyone tell me why my dual boot  (Win10/Ubuntu) system resets the system clock to UTC? The clock seems to work fine in Ubuntu displaying the correct time, but when I boot into Win10 the clock is 5 hours off - reset to UTC. Of course I can change the time back to local time and that works fine, but then when I boot into Ubuntu and back into Win10 the clock has returned to UTC. Is there a setting in the BIOS that will keep the clock on local time?

---

### Post by TheFu on 2020-04-28
Windows has historically used local time from the Bios.  That hasn't been required for a long time. Windows supports using UTC in the BIOS too. We just have to tell it.

Unix has historically used UTC since most Unix systems are networked and have been about 50 yrs. Linux can use either from the BIOS, as can MSFT, just be consistent with all the OSes booting on the machine.

I would change Windows to use UTC, if it was me.  Seek out a how-to from a Windows forum.  Something like "windows UTC hardware clock" would be my search.
Web search with those terms found these:

[https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/](https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/)
[http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/](http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/)
[https://askubuntu.com/questions/232405/how-do-i-set-my-clock-in-windows-to-utc-localtime](https://askubuntu.com/questions/232405/how-do-i-set-my-clock-in-windows-to-utc-localtime)

No need to get any extra application for either platform.

IME, Windows has a terrible problem keeping time since 1995. Having time correct to within 0.01 ms is a solved problem in the Unix world and has been longer than I've used Unix .... 30+ yrs.  

I have a Windows system running on real hardware that is always plugged in and runs 24/7 most of the time.  I has never kept the correct time and time would drift. It was always firewalled, but connected to the internet, so it should have access to internet time services.  Windows used to reset the time once a week, but that wasn't enough to be accurate to 1 minute. I changed the update period to daily.  Nope. Still not good enough.  Changed it to 12, 6, 4, 2 hours and got my expectations that time should be accurate to within 1 second if I was going to this trouble.  Still, the Windows machine time drifted. Sometimes as much as 5 minutes in an hour.  None of my other systems had any issue keeping sub-second accurate time, but both Windows systems couldn't.  

In the early 2000s, I worked for a huge corporation. We had MSFT engineers on-site for help solve issues.  At the time, we couldn't get time on all the desktops to be accurate within 1 minute and people were chronically showing up to meetings late.  The official answer from MSFT was that AD/DHCP was only designed to be accurate within +/- 5 minutes.  WHAT!??????  That was the answer we got.  Even on a fast, corporate, network, run by a (cough), world-wide networking company, our desktops couldn't have the correct time?  Further, MSFT wouldn't fix it. 

So, I setup a NTP server on my LAN at home and told the Windows systems to sync time from it every 1, then 30 min, then 15 min.  Finally, the Windows systems were keeping time to within 1 second accuracy ... if they were forced to sync every 15 minutes.  Crazy.

I should mention that one of those computers running Windows was converted to running Linux. Changing the OS should have nothing to do with keeping accurate time, right? After all, it is a little watch battery that keeps the RTC - real-time-clock - working and accurate.  Wrong.  Under Linux, that machine has always had and maintained correct time. Correct enough that it is the LAN time server here and has been since 2010. It is also the LAN backup server, so a fairly important machine.

Hopefully, the OP will **mark this thread as SOLVED** using the thread-tools button near the top.

---

### Post by lwalper on 2020-04-29
OK, so I set the clock to Win10 to UTC and, of course it's 5 hours off. What do I do? Set it to UTC and then adjust for -5 to read the time correctly?

---

### Post by CelticWarrior on 2020-04-29
There are two solutions for that, pick your favorite. I usually change it in Windows:
[https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)

---

### Post by TheFu on 2020-04-29
> **CelticWarrior said:**
> There are two solutions for that, pick your favorite. I usually change it in Windows:
[https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)

The OP already did that.  Hopefully, by now, he's figured out that Windows needs a setting that says "use UTC with the HWclock", googled for an answer and found it on a Windows forum/blog somewhere.

---

### Post by lwalper on 2020-04-30
OK thanks everyone. I found a workaround ... a free app called Time Sync. Installed it in Win10. Seems to work great.

[https://www.speed-soft.de/software/time_sync/details/download.php?language=en](https://www.speed-soft.de/software/time_sync/details/download.php?language=en)

---

