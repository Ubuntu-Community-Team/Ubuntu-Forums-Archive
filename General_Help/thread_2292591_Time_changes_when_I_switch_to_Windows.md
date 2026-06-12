---
title: "Time changes when I switch to Windows"
date: 2015-08-29
forum: General Help
---

### Post by grandpavic on 2015-08-29
I have a dual boot system, ubuntu and Windows 10 now (formerly Win 7). After I have been running ubuntu and then switch to windows my time of day clock always gets adjusted by I think 5 hours. It is turned forward by 5 hours. Something in the change over between the two operating systems is causing the clock to change. 

Any ideas?

---

### Post by SeijiSensei on 2015-08-29
You probably have different time zones set for the two operating systems.  One of them, Ubuntu probably, is likely to be using UTC (what was known as "Greenwich Mean Time"), while Windows is set to your local time zone.

Are both OSs using synchronization to network time servers?  What is the time of the hardware clock?  Use the "hwclock" command at a terminal prompt.  I suspect Ubuntu is resetting the hardware clock to UTC when it is shutdown.

---

### Post by grandpavic on 2015-08-29
> **SeijiSensei said:**
> You probably have different time zones set for the two operating systems.  One of them, Ubuntu probably, is likely to be using UTC (what was known as "Greenwich Mean Time"), while Windows is set to your local time zone.

Are both OSs using synchronization to network time servers?  What is the time of the hardware clock?  Use the "hwclock" command at a terminal prompt.  I suspect Ubuntu is resetting the hardware clock to UTC when it is shutdown.

Thank you for your help on this. The problem turned out to be in Windows.

Even though the time zone was correct and the the system was synchronizing with the internet there was another setting that I had never investigated before called region. Somehow the region was set to the UK instead of Canada. So I think it is now fixed.

Well its still not fixed. I ran hwclock and it returned a time that was about 6 hours slow for my time zone. I then left it for about 4 hours and ran hwclock again and lo and behold it came back with the correct time. 

I am running ubuntu at the moment. I will switch to Windows to see what time it is!

---

### Post by monkeybrain20122 on 2015-08-29
Probably because hardware clock is being reset and it is used by both but interpreted differently. I remember vaguely having that problem when dualbooting with XP a few years ago but never bothered to look into it since I never booted into XP except for updates (and got rid of it for good soon after)

[http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot](http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot)

---

### Post by grandpavic on 2015-08-29
Well I am back in Windows and the clock is off by 4 hours. So when I leave ubuntu it appears that the hardware clock is being set to UTC. 

So I guess the new question is how do I stop that from happening?

Or, how do i tell both systems that the hardware clock is set on UTC.

---

### Post by yetimon_64 on 2015-08-29
>  Or, how do i tell both systems that the hardware clock is set on UTC.                 

To stop this happening on this dual boot laptop I have told Ubuntu to _*not use*_ UTC by changing "UTC=" in the file /etc/default/rcS to "no", then I ran "tzselect" to make sure my Ubuntu system is set to my local timezone.

I am not sure how useful or difficult it is to change in Windows but as Windows by default uses the local timezone I altered Ubuntu to match it by the above method.

Some info on Ubuntu time setting is [[COLOR=#0000ff]--here--.[/COLOR]]("https://help.ubuntu.com/community/UbuntuTime")
Section 4 down the page a bit "Multiple Boot Systems Time Conflicts" at the bottom has a part titled "Make Linux use 'Local' time"

Some advice from the above link, in section 4, is ...
> Changing Linux to use local time is easier and more reliable than changing Windows to use UTC, so dual-boot Linux/Windows systems tend to use local time.

---

### Post by Yellow Pasque on 2015-08-29
I fixed Windows (7) rather than tampering with my other OS's. [https://wiki.archlinux.org/index.php/Time#UTC_in_Windows](https://wiki.archlinux.org/index.php/Time#UTC_in_Windows)
That same link also claims Ubuntu will automatically set itself to use local time if Windows is detected during install, but apparently that didn't happen for you.

---

### Post by yetimon_64 on 2015-08-30
> ..but apparently that didn't happen for you. 
Maybe it should have; when setting the time options with the installer I vaguely remember seeing a tick box where you can tell the Ubuntu system to use UTC or not. 

I think I may have ticked the box there and then when booting to windows later on and switching back to Ubuntu noted the time offset. I then used the /etc/default/rcS and tzselect method to get it all realigned.

Though on checking 'System Settings' > 'Time and Date' once installed, I can't see any option to alter the UTC setting. Seems only the installer alters that setting via the GUI.

---

### Post by grandpavic on 2015-08-30
> **yetimon_64 said:**
> To stop this happening on this dual boot laptop I have told Ubuntu to _*not use*_ UTC by changing "UTC=" in the file /etc/default/rcS to "no", then I ran "tzselect" to make sure my Ubuntu system is set to my local timezone.

I am not sure how useful or difficult it is to change in Windows but as Windows by default uses the local timezone I altered Ubuntu to match it by the above method.

Some info on Ubuntu time setting is [[COLOR=#0000ff]--here--.[/COLOR]]("https://help.ubuntu.com/community/UbuntuTime")
Section 4 down the page a bit "Multiple Boot Systems Time Conflicts" at the bottom has a part titled "Make Linux use 'Local' time"

Some advice from the above link, in section 4, is ...

Thank you for this. Setting rcs to no seems to have been the cure.

---

### Post by yetimon_64 on 2015-08-30
> **grandpavic said:**
> Thank you for this. Setting rcs to no seems to have been the cure.

You're welcome. It's good to hear it worked for you :). Could you please mark the tread as "Solved" from the Thread Tools drop down menu just above your first post? Cheers, yeti.

---

