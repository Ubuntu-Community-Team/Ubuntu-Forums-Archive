---
title: "My clock won't update from internet - in libraries."
date: 2014-07-21
forum: General Help
---

### Post by arnicainthemembrane on 2014-07-21
This is an odd problem. I've got ubuntu 12.04 on an Asus Eeepc 1050HA. And lately it's clock won't set to the internet, but only in library wifi zones, where you have to confirm that you're going to follow various rules to be on the network, etc. Invariably it gives some date in early 2001, and when I try to manually reset it it can only be done one day at a time, impossibly time consuming. This I discovered when I couldn't get online in libraries, Firefox thinking a certificate had been revoked or whatever. Now I just open up BIOS when I start the computer and set the time and date there, each time I log in on a library network. This seems to work to get me online, but the time and date still won't set properly. sudo dpkg-reconfigure tzdata and hwclock just reflect the time and date I set in BIOS. 

Any suggestions?

thanks

---

### Post by ajgreeny on 2014-07-21
What happens if you try to ping one of the ntp servers from the library; does that work, or are all attempts failures?

---

### Post by sammiev on 2014-07-21
If you are using a firewall you will need to have port udp 123 open.

---

### Post by SeijiSensei on 2014-07-21
After you have set the clock in the operating system, synchronize your on-board hardware clock with the command:
```
sudo hwclock --systohc
```
If the on-board clock fails to keep time, you need a new [battery]("http://www.amazon.com/ASUS-EEE-PC-1008HA-1005HAB/dp/B005J1T5YM").

---

