---
title: "Superblock last write time in the Future"
date: 2007-03-19
forum: General Help
---

### Post by Chazall1 on 2007-03-19
I have Edgy 6.10 on one HD and Win XP on a separate HD. I was Dual Booting on a simgle HD. I was reading the posts and the Time change took about 3 days to take effect. IWhen I run the
sudo zdump -v /etc/localtime | grep 2007 I get the same output on the 1st page. My XP had the correct  time first and I changed my time manually in Edgy, Adjust Date & Time and selected Synchronize Now and set my time up by one hour. In the past couple of days If I boot back into Edgy, I get a forced Fsck on /root, "Superblock last write time is in the future" and it will be fixed.  I would have to re-boot back into Edgy
I ran
sudo /etc/network/if-up.d/ntpdate 
Mar 19 10:17:49 localhost ntpdate[6447]: step time server 82.211.81.145 offset 2.722933 sec
My time is Eastern, UTC=No. My XP has the correct time and Edgy Has the correct time, But I still get the Error in root  "Superblock last write time is in the future"

Any Suggestions ?
Thanks

---

### Post by jondecker76 on 2007-05-03
i have the exact same problem, but it only happens from time to time

---

