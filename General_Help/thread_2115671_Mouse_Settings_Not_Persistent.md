---
title: "Mouse Settings Not Persistent"
date: 2013-02-13
forum: General Help
---

### Post by mooreted on 2013-02-13
I am running Ubuntu 12.10 x64 and usind a Razer Death Adder mouse. The mouse cursor was way to fast for non-gaming use so I use the following script to slow it down:

xinput --set-prop "Razer Razer DeathAdder" "Device Accel Constant Deceleration" 5
xinput --set-prop "Razer Razer DeathAdder" "Device Accel Velocity Scaling" 1

The trouble is; several times a day that setting gets lost and I have run the script again.

What daemon or setting would be overriding my mouse settings and how can I make it more persistent?

---

