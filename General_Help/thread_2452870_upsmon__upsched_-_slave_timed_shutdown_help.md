---
title: "upsmon / upsched - slave timed shutdown help"
date: 2020-10-29
forum: General Help
---

### Post by stevenjrees on 2020-10-29
I have an APC connected to a master freenas device.
I have a desktop connected to a separate dumb ups with a battery that lasts up to 1hr. 

i want to use upsmon slave on the desktop, to be triggered for a power failure by the freenas master, 
to then shutdown after 20min if power has not been restored. 

I have struggling to figure out the correct config for 
upsmon
upssched.conf
upssched-cmd 

can i do this without a heartbeat UPS? Can someone help with the correct config please.

---

