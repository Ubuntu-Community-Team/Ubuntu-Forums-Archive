---
title: "HP M2727 printer status Filter-failed"
date: 2016-10-07
forum: General Help
---

### Post by leunam12 on 2016-10-07
Hi, I have an HP M2727 connected to the network and it has been working flawlessly until a couple of days ago that I started getting this filter-failed error and now I can't print. I have rebooted the computer and the printer. I have verified that the printer is getting the right ip address and I can ping that ip address from my computer and get a response, so I don't know what went wrong. I don't have this printer installed with hplip, but is has worked very well until now.

---

### Post by howefield on 2016-10-07
No further clues in the cups error log ?

---

### Post by leunam12 on 2016-10-07
do I have to change the log level to debug and attempt to print again?

---

### Post by howefield on 2016-10-07
I was thinking about having a look in 

```
var/log/cups/error_log
```

if you haven't already.

---

### Post by leunam12 on 2016-10-08
Edit...

I removed the printer and installed it again and now it's working

---

