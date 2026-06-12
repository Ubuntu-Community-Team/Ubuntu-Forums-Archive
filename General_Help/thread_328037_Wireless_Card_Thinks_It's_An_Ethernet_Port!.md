---
title: "Wireless Card Thinks It's An Ethernet Port!"
date: 2006-12-30
forum: General Help
---

### Post by kbaum on 2006-12-30
My laptop was running Dapper before, and the wireless worked fine. But after upgrading to Edgy with the upgrade manager, my wireless card thinks it's an ethernet port, and I can't get online! ](*,) Now in networking it shows the actual ethernet port (wth0) and the wifi card (wlan0) but they're both wired connections. How do I fix this? :-k

---

### Post by fragos on 2006-12-30
Perhaps when you upgraded its also neccessary to re-install the packages you installed for wireless in Dapper.  There is after all a new kernel.  We need information to even begin to help you.  What wifi card are you using and what chipset is on it.  lspci can help you get that.  The output of ifconfig and iwconfig would also be helpful.

---

