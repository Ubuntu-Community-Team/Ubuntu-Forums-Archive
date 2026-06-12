---
title: "Changing RPM of Case Fan"
date: 2013-06-15
forum: General Help
---

### Post by Kodeine on 2013-06-15
My exhaust fan is from Antec and has a neat hardware switch to toggle between low, medium and high fan speeds although my intake fan does not has such luxury. When I'm playing games like l4d2 my CPU temperature doesn't go above 41c. All the while the intake stays at the same, slow, speed.

I've found that the RPM of my two fans is either written (and read?) from the file */sys/devices/platform/it87.552/fan_input2*. I don't know if changing that file will result in the fan speed altering. The intake fan is connected via a three pin connector to a four pin header. How do I manually adjust the speed of my intake fan?

---

### Post by CatKiller on 2013-06-15
> **Kodeine said:**
> When I'm playing games like l4d2 my CPU temperature doesn't go above 41c. All the while the intake stays at the same, slow, speed.

If you're getting low temps with a slow fan, that's great. Upping the fan speed at that point just gets you noise for no benefit.

> 
The intake fan is connected via a three pin connector to a four pin header. How do I manually adjust the speed of my intake fan?

I'm not sure that you can adjust the speed in that configuration. Three-pin fans use voltage regulation to adjust the speed and four-pin ones use pulse-width modulation. If you've got another three-pin header on the motherboard, that would probably work better.

You don't need to manually control the speed. There's a utility in the repositories called *fancontrol* that will read the temperature from a given sensor and adjust the speed of a given fan according to criteria that you pick.

---

### Post by Frogs Hair on 2013-06-15
You may want to find out more about the software at the link if you are bothered by the fan . I haven't used the program and no nothing about it.    [http://sourceforge.net/projects/fancon/](http://sourceforge.net/projects/fancon/)

---

