---
title: "trying to set time manually but it keeps changing by 2 hours"
date: 2016-09-05
forum: General Help
---

### Post by a-you on 2016-09-05
I had set the time manually when I installed xenial back in April and it was working just fine. Then I went out of town for a while and temporarily set the time manually to the new time zone. While there the time would be set wrongly by 2 hours. Now that I'm back and I try to set the time it continues to have this problem where when I reboot the time is off by 2 hours. I have no idea why.  If anybody could help I'd much appreciate it.  I'd prefer not to use ntpd. Just setting the time manually would be fine with me, but now it's not working.   I have a dual boot with windows 7 but I never use that (why would I ;-) ).  I definitely didn't intentionally change the time settings via windows, that's for sure.  Thanks in advance for any help.

---

### Post by Jimysbil on 2016-09-05
You can check [this]("http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot") out.

I had the same problem and I just changed the time setting on Ubuntu.

---

### Post by a-you on 2016-09-06
Thanks Jimysbil. That's a solution. Just that I'm still surprised that it was working perfectly for months, then only broke after I set it to a different city. Would be nice not to have to set ubuntu to local time. If that's the only solution though then I don't mind doing it.

---

### Post by a-you on 2016-09-06
Whew just got it to work without having to set the hardware clock to local time. ```
date --set='date and time in UTC' --utc
``````
hwclock --systohc --utc 
``` Now when I reboot the clock is correct. Both of those commands have to be run as root (sudo).  I should add that prior to that I had done ```
dpkg-reconfigure tzdata
``` (as root) which probably played a part in the solution by setting the timezone I'm in. Also I believe that it had gotten screwed up because I had briefly booted into windows to change some power settings that I don't seem to have access to from ubuntu. It's possible that the --utc option to date is superfluous. I'm not sure about that. But I believe that the --utc option to hwclock is necessary if you want the hardware clock to be set to utc time instead of local time.  By the way in case it's not obvious where it says 'date and time in UTC' I mean set it to your current date and time.

---

