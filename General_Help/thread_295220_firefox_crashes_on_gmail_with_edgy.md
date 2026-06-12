---
title: "firefox crashes on gmail with edgy"
date: 2006-11-07
forum: General Help
---

### Post by kamilczauz on 2006-11-07
when i open up firefox and login to my gmail acocunt, it closes it self and dissappears... anyone else having this problem?

thinkpad t23 with ubuntu 6.10

---

### Post by reclusivemonkey on 2006-11-08
> **kamilczauz said:**
> when i open up firefox and login to my gmail acocunt, it closes it self and dissappears... anyone else having this problem?

thinkpad t23 with ubuntu 6.10

Gmail/Firefox too works fine for me on Edgy on a Desktop PC. Try launching firefox from the console see if you get any helpful error messages.

---

### Post by madjid on 2006-11-20
Hi,

Same pb here with kubuntu. It crashes when gmail is opened. It works fine though when javascript is disabled. ](*,) 

Anyone who has a solution, please share. 


kubuntu 6.10 on laptop hp pavillon dv5000t

---

### Post by feign on 2006-11-20
Try clearing your cache.

This necessarily won't resolve your problem but it will force Firefox to create a new session each time, that might help.

[http://www.ubuntuforums.org/showthread.php?t=286508&highlight=session](http://www.ubuntuforums.org/showthread.php?t=286508&highlight=session)

---

### Post by madjid on 2006-11-20
Clearing the cache doesn't help. It crashes even if the session is new.

---

### Post by feign on 2006-11-20
Seems like the same problem is being reported in another posting..

[http://www.ubuntuforums.org/showthread.php?t=302349](http://www.ubuntuforums.org/showthread.php?t=302349)

---

### Post by dad311 on 2006-11-20
I just did a new install last night with Automatix updates, no issues with gmail.

---

### Post by feign on 2006-11-20
Would that include the JRE?  What about others was JRE installed, if so how?

---

### Post by madjid on 2006-11-21
:) 
I fixed it by editing ~/xorg.conf and changing the default color depth from 16 to 24. Found it on a firefox forum. Hope this will help.

---

