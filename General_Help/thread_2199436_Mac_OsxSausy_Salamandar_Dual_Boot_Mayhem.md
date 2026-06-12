---
title: "Mac Osx/Sausy Salamandar Dual Boot Mayhem"
date: 2014-01-13
forum: General Help
---

### Post by KaikeaBlakemore on 2014-01-13
Hey, 

I have a dual boot Macbook with 13.10 and since I updated both my partitions are lagging to the point of requiring force shutdown after 10-15 minutes, especially when running consuming programs/streaming. I suspected damaged RAM but got an "OK" when I ran memtest, said RAM was normal and functioning (it was updated once a year and a half ago, no problems till the saucy update). 

Otherwise I made two large N00bie mistakes that may be contributing--- laptop took a 3foot drop and couldn't find the operating system upon boot last month. It seems fixed now (usually turns up with Refit when I boot) but will do the Osx flashy file question mark thing after force shutdown now-- this seems to be resolved if I unplug the computer and leave it sitting for awhile then reboot (my battery doesn't charge, so could be comparable to leaving it sitting with the chord and battery removed, if that factors). 

I also --ack, don't yell-- deleted two tiny partitions that were flagged as "unknown" and had little or no space on them. (Yes, I ignored the screaming intuition saying "stop!!!" when I did it) was trying to clean up after a new install left me with what looked like twice as many partitions as I previously had. Should have come here first and asked what they were. 

Anyway, I'm thinking I will do a fresh clean install and hope the missing pieces will be remedied. RAM on memtest says everything's fine, don't know if it ever misses anything. 

Please share any computer fixing ideas... I can boot on either ubuntu or mac partitions, but my computer doesn't stay working for long... :confused:

---

### Post by tgalati4 on 2014-01-14
Look in the log files for errors (/var/log).  It's possible there are other problems, like a loose ribbon connector that could cause IOWaits with the hard disk.  The only thing you didn't do was drop your mac in a swimming pool.  Now that would be a challenge to fix.

---

