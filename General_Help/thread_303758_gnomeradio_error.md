---
title: "gnomeradio error"
date: 2006-11-20
forum: General Help
---

### Post by xenoalien on 2006-11-20
I try to run Gnomeradio and I get an error that says 
"could not open device "/deve/radio" !" 
"Check your settings and make sure that no other program is running /dev/radio. Make also sure that you have read-access to it"

I checked and no other application was using /dev/radio. But how do I make /dev/radio read accessible?

---

### Post by xenoalien on 2006-11-20
bump

---

### Post by napzilla on 2007-08-16
This may seem idiotic, but it turned out to be the root of my troubles. Is /dev/radio actually *present* on your system? It is not present on mine, and I haven't figured out how to configure the hardware to get it there yet.

---

### Post by fragos on 2007-08-16
I've a WinTV 150 with a radio tuner.  /dev/radio0 is generated for me.

---

