---
title: "Monitor issue after daily update for 18.04"
date: 2018-12-09
forum: General Help
---

### Post by rapidrob on 2018-12-09
I did a daily update yesterday for Ubuntu 18.04 and now for the first time,when I shut the PC down, I get a " Check source cable" error on the monitor that does not go away even though the PC is fully off and several minutes have passed. 
This would be the same as if I unplugged the cable with the monitor on but not hooked to a computer. This has never happened before and started after the software update.
I have checked the GPU board setting and the monitor settings with nothing out of the ordinary. The cable is new and both ends are tightly screwed down. Changing to a 2nd HDML port did not help the problem.
ZOTAC NVIDIA GeForce 9800GT ECO
Samsung SyncMaster 204b
HDML cable

---

### Post by rapidrob on 2018-12-09
The drivers for the GPU are what are recommended.

Nvidia binary driver-version 340.107 from nvidia-340 ( proprietary,tested)
" this device is using the recommended drivers"

---

### Post by CatKiller on 2018-12-09
Nvidia are currently in the process of changing how they handle turning the monitor off. You could either delve into sending bug reports to them about it, or simply turn the monitor off after the machine has shut down. I'm not aware of a configuration option yet to change how their driver handles it.

I take it back:

> Added a new X configuration option "HardDPMS" which is disabled by default, but can be enabled to put displays to sleep with modesets rather than VESA DPMS. This may fix some displays that fail to sleep when DPMS becomes active. "HardDPMS" will be enabled by default in a future release.

I don't know that that option will be enabled for the driver you're using, but that's the setting that will control it.

---

### Post by rapidrob on 2018-12-09
I just noticed that when the monitor goes to sleep after one hour set by software, the same error shows up.

---

### Post by rapidrob on 2018-12-12
After todays Ubuntu updates, the monitor is back to working in a normal manner. I had gone over to NVIDIA and asked a question and all I got was " The graphics card must be bad,replace it".
Not much help there.

---

### Post by CatKiller on 2018-12-12
Well, good to hear that it's working for you again :neutral:

---

