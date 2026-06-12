---
title: "[SOLVED] ATI Graphics Card"
date: 2007-11-07
forum: General Help
---

### Post by AK47Jazz on 2007-11-07
I just got my wireless working and now I have a new problem.
When I try to enable my restricted graphics driver it gives me this message every time.

"The software source for the package

   xorg-driver-fglrx

 is not enabled."

I REALLY need help with this. Can someone answer my question?

---

### Post by Maestro23 on 2007-11-07
Got all your sources enabled? System>>Admin>>Software Sources

Proprietary Drivers must be enabled. Then reload.  Try your driver again.

*Congrats on getting your wireless card working.  That's always a stubling block for some. :smile:

---

### Post by AK47Jazz on 2007-11-07
What you have told seems to be the fix, but when i am trying to download the package information it just stalls and doesn't download at all, any answers?

---

### Post by Maestro23 on 2007-11-07
> **AK47Jazz said:**
> What you have told seems to be the fix, but when i am trying to download the package information it just stalls and doesn't download at all, any answers?

Post your sources.list file.

In a terminal:

> cat /etc/apt/sources.list

Copy/Paste the file here.

---

### Post by AK47Jazz on 2007-11-07
EDIT: Got it working, had to set my network proxy under prefences, 

thanks for the fast help

---

### Post by Maestro23 on 2007-11-07
> **AK47Jazz said:**
> EDIT: Got it working, had to set my network proxy under prefences, 

thanks for the fast help

Good deal man.  Don't forget to mark this SOLVED using the Thread Tools.

Thanks.:)

---

