---
title: "power-manager doesn't detect my battery."
date: 2007-10-24
forum: General Help
---

### Post by phibit on 2007-10-24
I have an HP dv2120ca laptop, running ubuntu GUTSY. When I had Feisty, the gnome-power-manager correctly displayed my battery state (either charging or discharging, and what percentage it was at).

After I upgraded to gutsy, the gnome-power-manager always indicates that my battery is charging under AC power, even though it's clearly not.

Here's my /proc/acpi/battery/BAT0/state:
```
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            0 mA
remaining capacity:      2160 mAh
present voltage:         11014 mV
```

So it IS being detected properly, and shows the corret 'charging state' and 'remaining capacity'...

Anyone else have this problem? Know a fix?

---

### Post by phibit on 2007-10-29
Another reason why this issue is a problem for me is because the CPU speed scaling I used to use to manage battery length is now gone.

As such, my CPU is always operating at 100% and this SUCKS my battery dry (dual core Turion is a power-monger).

What can I do about this?

---

### Post by lawentzel on 2007-10-29
I am having the exact same problem.  I had installed Gutsy when it was in beta and it worked initially.  Several updates later it is no long working properly.  It seems like when ever there was a kernel update, the power manager would start working again until I rebooted the system.  At which point it died.  I have verified that the power manager is running.  I don't know how to get that data you had provided.  I do have pictures showing the different icons when the power manager WAS working and now.  They can be seen at:

[My power icons.]("http://www.geocities.com/lawentzel/powericon.html")

Notice the working icon has the "reboot" symbol to the left of it.  After I rebooted, it quit working again.

---

