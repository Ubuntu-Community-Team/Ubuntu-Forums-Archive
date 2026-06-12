---
title: "Changing mouse sensitivity on startup"
date: 2013-07-07
forum: General Help
---

### Post by Ladkipz on 2013-07-07
Hey guys,

I have a Razer Deathadder and am trying to reduce the sensitivity of the mouse on startup to something lower than the GUI allows. In accordance with the help instructions, I have written and run the following code and it works fine when executed.

```
#!/bin/sh
xinput set-prop 11 "Device Accel Constant Deceleration" 4.85
xinput set-prop 11 "Device Accel Velocity Scaling" 1

```

[B]I have two problems with this at the moment:
[/B][LIST=1]
[*]Often the prop number changes on various boots. So even if I could make it execute at startup, I usually need to change the prop number anyway. I tried setting 11 as the device name with no luck.
[*]How do I make this script run on startup and also on resume from sleep. Please have patience here as I am no expert with ubuntu.
[/LIST]

Thanks heaps.

---

### Post by CatKiller on 2013-07-07
When I was playing with similar I discovered that you can put those kinds of settings in your xorg.conf.

Otherwise, you can call the script from ~/.xinitrc for when X starts, or in Startup Applications for when you log in. You'll need to experiment to see if you also need to call it when you resume, but there are a bunch of scripts that get run on resume so it shouldn't be too difficult to add your script to the list.

---

