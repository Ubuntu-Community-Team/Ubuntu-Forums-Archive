---
title: "Psensor questions"
date: 2012-12-20
forum: General Help
---

### Post by mystmaiden on 2012-12-20
I have been having issues with my computer randomly shutting down while watching any streaming videos so cleaned it well and downloaded psensor to see if I could pinpoint the issue. It looks like it may be the hard drive because the cpu was within mid range most of the time. But it shows dev/sda as having a minimum temp of 36 C and maximum of 37 C. My question is are the minimums and maximums determined by psensor or by something in bios. The hdd temp doesn't have much leeway at 1 degree difference. I'm not sure what's safe for hdd, my research seems to indicate 37 C is pretty low.

any enlightenment would be great!!

mystmaiden

---

### Post by TOMBSTONEV2 on 2012-12-20
I think (someone please correct me if I'm wrong) the min and max temperatures are what the temp for the specific device has been at whilst Psensor is open. So if your hard drive hit 5504 C than your max would say 5504 C. I have always operated with this understanding of Psensor. Note my hard is at 39 C, which is pretty normal.

If your hard drive ever reaches 5504 C you may want to check if you are computing on the surface of the sun. :popcorn:

---

### Post by mystmaiden on 2012-12-20
Thanks for the reply, that makes more sense than what I was thinking.

I looked around in bios and did not find anything that would indicate it measures the hdd temp and the cpu temp shutdown was disabled so...hmm no actual idea why its shutting down. I guess the next step is a more thorough cleaning and pulling the cpu to replace the thermal paste. That and I'll try to avoid the surface of the sun when computing! \\:D/

---

### Post by TOMBSTONEV2 on 2012-12-21
Sounds like a good plan, also you ma want to check the log file viewer.  Dash > Search "log file" and it will pop up. Perhaps there is something in there to aid you in diagnosing your computer.

---

### Post by jeanfi on 2012-12-22
Hello,

> **mystmaiden said:**
> My question is are the minimums and maximums determined by psensor or by something in bios.

I can confirm that the min and max columns of the table are the min and max values of the sensors registered by Psensor since its startup. It is NOT the safe or recommended limits of the HW.

Note that you can setup manually a low and high threshold for each sensor to raise an alarm by using Psensor > Sensors Preferences > Alarm.

Usually, at least in a correctly cooled desktop computer, the  temperature of a HDD does not vary a lot, you can expect only  few  celcius difference. A temperature lesser than 40C is totaly normal for  most disks (SSD has a lower temperature).

After your computer has rebooted you should take look at the /var/log/syslog.1 file, you will probably find the reason. As the HDD temperature sounds good, there is more chance that it is due to CPU, GPU temperatures or other HW issues (like a memory bank).

---

### Post by jeanfi on 2012-12-22
.

---

### Post by mystmaiden on 2012-12-27
Thank you so much Tombstone and jeanfi for the replies. I finally decided it was the power supply and changed that out (first time to change a psu, I was nervous!), The shut down issue is gone and psensor is looking pretty normal now.


mystmaiden

---

