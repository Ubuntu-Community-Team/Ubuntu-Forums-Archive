---
title: "Ubuntu Keeps crashing after 24.04 update"
date: 2024-05-22
forum: General Help
---

### Post by karpontinisjohn on 2024-05-22
Hi, i have ubuntu installed along with windows dual booted on my Dell Latitude e6410. After the 24.04 update ubuntu crashes a few minutes after booting. (screen freezes, mouse locks up, no hdd activity). Windows seems to work normally. I tried to reinstall it using a live usb of 24.04 and the live usb also crashed in the same exact way. Tried to use safe graphics and it installed just fine (no crashing). After the reinstallation it started crashing again. I was able to go to proprietary drivers before it crashed and none are in use. I should also point out that ubuntu worked just fine before the update. Any tips?

---

### Post by deadflowr on 2024-05-22
*Thread moved to **General Help***

---

### Post by karpontinisjohn on 2024-05-23
The biggest issue is that I have very little time before the system freezes (sometimes less than a minute )so there is not a lot of things I can check... Any advice?

---

### Post by karpontinisjohn on 2024-05-23
Any help would be really appreciated since i really need the computer to be operational again

thanks

---

### Post by hex-m on 2024-07-11
I had a similar problem and for me it was xwayland crashing. So a workaround would be to disable wayland and use X11 instead.

---

