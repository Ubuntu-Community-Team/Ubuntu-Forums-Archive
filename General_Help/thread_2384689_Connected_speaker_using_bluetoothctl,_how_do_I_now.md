---
title: "Connected speaker using bluetoothctl, how do I now set up audio sink"
date: 2018-02-10
forum: General Help
---

### Post by mycomputertips on 2018-02-10
I managed to pair my bluetooth speaker using bluetoothctl via the terminal, so that's one hurdle completed.
I'm stuck on getting audio to play through the speaker now. Been looking around various sites and I'm even more confused.

---

### Post by jeremy31 on 2018-02-10
Check results for ```
pactl list short | grep blue
```
You will want to see module-bluetooth-discover and then after pairing the device should show in Sound Settings

---

