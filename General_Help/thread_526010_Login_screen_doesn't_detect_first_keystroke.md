---
title: "Login screen doesn't detect first keystroke"
date: 2007-08-15
forum: General Help
---

### Post by kh1116 on 2007-08-15
Hi, I'm not sure if anyone else experiences this, I did a forum search with no results. On the login screen, every time I try to write my name the first letter I type doesn't get detected. Not really much of a problem, but it does get annoying. Anybody else have this problem? I am using a wireless keyboard if that matters, but have no trouble with it in windows.
Thanks Kevin

---

### Post by kh1116 on 2007-08-15
bump

---

### Post by barisy on 2007-08-15
i think it's your wireless keyboard, there has to be some kind of inconsistency when you use wireless one's try the corded one .. Are you having problems on USB devices?

---

### Post by kh1116 on 2007-08-16
no problems with any of my usb devices, my printer and mp3 player both are usb.

---

### Post by CentralX on 2007-08-17
Hi,

Are you using a Core 2 Duo? If so, it might be related to the so called C4 power state of your processor. When the CPU is idle for a certain amount of time it quickly throttles back to C4, a low power consumption mode. It might be so, that it wakes up on the first keystroke and therefore "forgets" to register the keystroke in the process. I'm using a Mac Core 2 Duo which also has this problem. I disabled C4 powerstate and have never experienced it again. Also, my laptop "whines" (an annoying buzzing noise) when in C4 power state (idle), so I had two reasons to disable it. I guess all might be related to poor power management implementation in current operating systems, because C4 is pretty new, power management software might not be fully optimized for it yet.

Regards,

CentralX

---

### Post by kh1116 on 2007-08-17
No, I am not using a core 2 duo, although what you have done for your computer seems like a good fix. I am using an AMD Duron 1000.

---

