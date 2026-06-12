---
title: "Citrix Client Error"
date: 2007-09-17
forum: General Help
---

### Post by gdamn on 2007-09-17
I get the following error when trying to open my citrix application connections:

"The server has disconnected.
This may be caused by failing to obtain a Microsoft Client Access License for a Windows server or the requested window size may not be supported by this server."

I assume my Remote Access License with the server has expired as this happens on my windows box from time to time and I have to go in and remove the registy entry for it and get a new license.  But I have no clue where that might be stored in linux.  Has anyone else experienced this issue and come up with a solution to fix it?  Thanks in advance for any help you can lend me!

---

### Post by Skrewdriver on 2007-09-25
try this at the terminal:
```
sudo mkdir /etc/icalicense
sudo chmod a+rw /etc/icalicense/

```

then log on to Citrix and see if it works

---

### Post by negated on 2007-10-24
I had the same problem in 7.04 x86 with ICA 10.1. The solution above however did not help; can anyone else confirm that this solution worked?

Thanks!

-S

---

