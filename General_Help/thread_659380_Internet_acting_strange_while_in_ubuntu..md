---
title: "Internet acting strange while in ubuntu."
date: 2008-01-05
forum: General Help
---

### Post by Mr.popo on 2008-01-05
While im in Ubuntu my internet seems to freeze or disconnect and it takes around 60 seconds to reconnect. This problem seems to occur randomly. I dont think theres a problem with my internet connecting because while im in vista it works perfectly. Do you have any idea why this is happening.

Thanks
Mr.popo

---

### Post by reckless2k2 on 2008-01-05
is this a wired or wireless connection?

---

### Post by lswest on 2008-01-05
during the time you lose connection, could you paste the output of ```
sudo iwconfig [name of card]
``` (if its wireless) or ```
sudo ifconfig [name of card]
``` if its a wired connection.  the name will be either wlanX or ethX or athX.  can be found out by running iwconfig or ifconfig without arguments.

---

### Post by Mr.popo on 2008-01-05
Im on a wired connection, with a router providing internet for my network. Next time I loose connection I shall past the ouput of that command.


Thanks
Mr.popo

---

