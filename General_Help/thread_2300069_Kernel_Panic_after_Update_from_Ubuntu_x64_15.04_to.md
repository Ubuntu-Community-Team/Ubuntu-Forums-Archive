---
title: "Kernel Panic after Update from Ubuntu x64 15.04 to 15.10"
date: 2015-10-23
forum: General Help
---

### Post by artur3004 on 2015-10-23
After the recent update, my Ubuntu won't start after it updated from 15.04 to 15.10, Device: Lenovo Yoga 13 3 with i5. 
Kernel Panic (blinking Caps Lock), recovery start won't work, either. I have file acces through windows with ext2fsd to copy the logs wichever you guys needed for more analysis. Already thanks for your help!

---

### Post by artur3004 on 2015-10-26
Nobody? Ubuntu starts without problems if booting with Linux 3.8, not with 4.2

---

### Post by vandammes on 2015-10-26
"Abandon all hope, ye who enter here." 

I'm trying to get Kubuntu 15.10 to run. Meanwhile, back to Mint 17.2 with Linux 3.13.  This newfangled stuff is not for me.

---

### Post by artur3004 on 2015-10-27
"dpkg --configure -a" fixed it. Only one command between kernel panic and everythings fine

---

