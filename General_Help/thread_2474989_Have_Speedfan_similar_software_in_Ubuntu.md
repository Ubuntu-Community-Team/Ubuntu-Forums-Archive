---
title: "Have Speedfan similar software in Ubuntu ?"
date: 2022-05-13
forum: General Help
---

### Post by aug7744 on 2022-05-13
Hello.
Other OS have an software SpeedFan that control fan speed and have taskbar icons showing CPU and HDD temperature.
Ubuntu have any software with same features ?
Thanks for reply.

---

### Post by TheFu on 2022-05-13
**psensor** - it isn't an icon, but it can be sized to a specific size.  I'd be surprised if **Conky** or **Glances** doesn't have an addon/plugin to show data too. Google found all sorts of information for Conky and a feature request for Glances.

But the ability to access sensor data is extremely hardware dependent.  I understand that lots of missing power, temperature, and fan data was added in 5.15 and 5.18 for AMD systems.
Intel systems generally have good sensor support.

[https://www.cyberciti.biz/faq/howto-linux-get-sensors-information/](https://www.cyberciti.biz/faq/howto-linux-get-sensors-information/) should get the CLI stuff installed. That's usually needed before the GUI stuff.

---

### Post by kurt18947 on 2022-05-13
> **aug7744 said:**
> Hello.
Other OS have an software SpeedFan that control fan speed and have taskbar icons showing CPU and HDD temperature.
Ubuntu have any software with same features ?
Thanks for reply.

Software that shows system information is not uncommon. I have something called 'system profiler' or 'hardinfo' via Synaptic. You may need to install something called 'lm-sensors'. if you're using gnome, search extensions for 'temp'. You'll get a few possibilities. I think those only show temps, voltage and fan speed. I don't know of anything that can be used to change fan speed for instance.

---

