---
title: "system tries to open file on each logon"
date: 2013-01-14
forum: General Help
---

### Post by marchelloUA on 2013-01-14
Hi all, 

It is wierd, I've opened some pdf file day before and then performed reboot. 
Now each time I logon the system tries to open that pdf file (from tmp space as far as I can understand) and reports error. 

How do I deal with that?

---

### Post by csillva on 2013-02-20
Under >system settings > Starup & Shutdown

Look for any pdf related applications in autostart, and under session management, under On login, change to "start with empty session"

---

