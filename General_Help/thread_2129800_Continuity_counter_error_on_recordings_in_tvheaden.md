---
title: "Continuity counter error on recordings in tvheadend"
date: 2013-03-27
forum: General Help
---

### Post by spacecakes on 2013-03-27
[COLOR=#484848][FONT=Lucida Grande]Hi, i get these Continuity counter error everytime i record, not when i watch livetv. And it seems to be more frequent when i record to my raid5 array and less frequent when i record to the OS ssd, any suggestions?
I asked this in the tvheadend forum but it seems pretty dead so iam trying my luck here instead :)

I have [/FONT][/COLOR][http://www.dvbshop.net/product_info.php/info/p2303_Technotrend-Budget-C-1501-CI---Second-Hand.html](http://www.dvbshop.net/product_info.php/info/p2303_Technotrend-Budget-C-1501-CI---Second-Hand.html)

Running ubuntu 12.04 with 3.4.0-030400-generic #201205210521 SMP Mon May 21 09:22:02 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux kernel

tvheadend version is 3.3.491 beta. Same problem with 3.2 stable.

Installed V4l drivers but nothing changed.

---

### Post by spacecakes on 2013-03-28
bump

---

### Post by spacecakes on 2013-04-10
I have not yet fixed this but i got a little bit more info. I get alot of these:
[76714.096054] saa7146: saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
[77832.120156] saa7146: saa7146 (0) saa7146_i2c_writeout [irq]: timed out waiting for end of xfer
[79197.479902] saa7146 (0) vpeirq: used 1 times >80% of buffer (163184 bytes now)
[79227.485184] saa7146 (0) vpeirq: used 7 times >80% of buffer (65612 bytes now)
[79257.498651] saa7146 (0) vpeirq: used 2 times >80% of buffer (65424 bytes now)

when i get the errors, any ides?

---

