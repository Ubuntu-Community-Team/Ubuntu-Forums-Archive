---
title: "Hybrid startup &gt; Showing GFX and running processes ?"
date: 2018-08-15
forum: General Help
---

### Post by GeordieJedi on 2018-08-15
Hi there guys.

I was wondering if there is a way to combine the standard loading screen
(showing the default Ubuntu gfx) and to also show the list of processes
as the computer loading.

I (am aware of) and have removed the "quiet splash" option, so that I can see the
processes as the computer loads.

I would love to have it like this -
1. Top 3rd of the screen, showing the start up gfx (possibly showing a progress bar).
2. The remaining 2/3rds of the screen, showing a list of the processed as they are loaded.

Is there any way to achive this at all ?
If there is, would you let me know how this is done please.

TIA for any help or advice.


Helpful information:

Hardware:
Laptop
Medion Akoya - E7214 (MD 98360)
17.3" Widescreen  /  Core i3 350M CPU  /  3GB Ram  /  320GB HDD  /
Intel HD Graphics

Software:
OS: Ubuntu 16.04.4 | LTS | (64 bit)
Kernel: 4.4.0-130-generic
KDE: 5.5.5

---

### Post by #&amp;thj^% on 2018-08-15
> **GeordieJedi said:**
> 

Is there any way to achive this at all ?
If there is, would you let me know how this is done please.



Dose this help?
```
journalctl -b > startup.txt
```
Or even this:
```
systemctl list-units --type service -all > startupservice.txt
```

---

