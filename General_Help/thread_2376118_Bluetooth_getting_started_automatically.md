---
title: "Bluetooth getting started automatically"
date: 2017-10-30
forum: General Help
---

### Post by meetdilip on 2017-10-30
16.04 + Unity. It started only recently. Could be a week at the most. Bluetooth gets enabled automatically in my laptop. The bluetooth icon changes to active. I doubt it has something to do with " Suspend " feature I am using when I stay away laptop for small periods. I tried to report a bug in launchpad. The process seems too complicated for me. 

Is there any fix available for this issue ? Thanks.

---

### Post by ajgreeny on 2017-10-30
There are various ways to do this; perhaps the easiest is to install bum, (BootUpManager) and disable it in that.

Alternatively, if you have no bluetooth hardware you can simply remove the bluetooth package with ```
sudo apt remove bluetooth
```

---

### Post by meetdilip on 2017-10-30
Bluetooth does not start on startup for me. It works as it should be until I suspend my PC. When I come back and resume, I find the Bluetooth is ON.

I have Bluetooth hardware and it works well.I use it at times as well. It getting switched ON by itself is taking its toll on battery life. I disable it manually when I notice. But, it should not get enabled without human interference, suspended or not.

---

### Post by Bucky Ball on 2017-10-31
Open 'Session and Startup', look for anything pertaining to bluetooth and disable it. Restart the machine. Any bluetooth activating?

Or, as above, remove the bluetooth software and restart. Good luck.

---

### Post by meetdilip on 2017-10-31
1. Couldn't find any entry through Dash for " Session and Startup ". There was **startup applications** though ( 16.04 ), which had no entries for Bluetooth

2. I want to keep Bluetooth and put it to use when required.

Thanks. :)

---

