---
title: "vmware in ubuntu edgy won't start"
date: 2007-01-06
forum: General Help
---

### Post by insane_alien on 2007-01-06
i just installed vmware in edgy(using generic kernel) with this howto ( [http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209) )and it installed fine. if i try to run it however, it does nothing. i get 100% CPU usage and nothing happens. i've left it for 30 mins and nothing happened. i ended it after that because i got worried about the heat.  ran it in terminal but didn't get any error message. can anyone help me get it running?

EDIT: got some help in IRC if you have the same problem run this command

LD_PRELOAD=/usr/lib/libdbus-1.so.3:$LD_PRELOAD vmware

---

