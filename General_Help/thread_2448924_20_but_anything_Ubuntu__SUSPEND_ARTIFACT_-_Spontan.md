---
title: "20 but anything Ubuntu : SUSPEND ARTIFACT - Spontaneous restart after shutdown"
date: 2020-08-16
forum: General Help
---

### Post by Kris_M on 2020-08-16
20 but anything Ubuntu : Spontaneous restart on menu shutdown or poweroff

Seems I found this before but...

This is a** suspend** artifact - 
can be reproduced with:

systemctl suspend

then poweroff by any means
it will spontaneously restart in about 3 secs.

I had menu/settings/Hardware/power management/power options/when lid is closed = suspend.

if change to anything (I chose lock screen) and then power off, it will not spontaneously restart

defaults are 
suspend when inactive for: Never Never
When lid is closed:  Suspend  Suspend

**Why does suspend do this??????????????????????????**

This has been true since I started playing with Ubuntu and offshoots since long long ago.

---

