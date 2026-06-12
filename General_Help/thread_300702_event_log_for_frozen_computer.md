---
title: "event log for frozen computer"
date: 2006-11-16
forum: General Help
---

### Post by Jan Hrbacek on 2006-11-16
Hi! Is there a way to find out what is happening with my computer immediatelly before it freezes?

Is there some logging file where this information is stored? 

If I restart the computer then dmesg only includes logs of events from the startup of the computer.

Are there any other log files? (I am sure they are, I just don't know their names...)

Thanks.

---

### Post by an.echte.trilingue on 2006-11-16
What kind of crash are you having?  What are you doing when you have freezes?

---

### Post by Jan Hrbacek on 2006-11-17
opening some pages at firefox

---

### Post by MJN on 2006-11-17
Graphic intensive? Could well be a video card/driver problem...
 
Unfortunately with sudden halts like this nothing is written to a lofile... however it hurts not to see what's in /var/log/syslog for the preceeding period.
 
Mathew

---

### Post by an.echte.trilingue on 2006-11-18
I would bet euros to dollars that it is the video card.  Will you post the contents of the file /etc/X11/xorg.conf and also the output from the terminal command "lspci"?

---

