---
title: "ADSL stoped working"
date: 2008-03-13
forum: General Help
---

### Post by peromalosutra on 2008-03-13
I have ADSL ruter attached to USB (SpeedTouch v530) and it all worked great for almost 2 years (first on Ubuntu 6.10, then 7.10), unill I started pppoeconf program from terminal to capture some screanshoots for a little guide that I was writing. While caputring screanshoots I noticed that my internet conection is not functioning, so I started pppoeconf again, trying to set i right, but there is no use. I have windows on the other partition and conection is working properly there (I'm forced to write this from windows), so the problem is somewhere in Linux, but I simply cannot find what's wrong. 

I cannot fin ppp0 in the output of ifconfig command, and after typing pon dsl-provider it sometimes apears in that output and sometimes not. Also, the internet conetction does apear sporadicaly, but most od the time it's not working. Very confusing.

Is there any way to delete all the things that are somehow related to making conection and to reconfigure it again, becouse i think I configured everything properly but it't just not working.

---

### Post by peromalosutra on 2008-03-15
I got around the problem by attaching ruter directly to network card (eth0) and setting it to DHCP.  Iz's now working fine, but I still don't understand why it didn't worked in the first place.

---

