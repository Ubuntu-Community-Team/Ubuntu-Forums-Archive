---
title: "Ubuntu 13.10 - Time Missing on Top Bar"
date: 2013-10-31
forum: General Help
---

### Post by tecknomage on 2013-10-31
**REF:** Ubuntu 13.10, GNOME Flashback desktop

_Occasionally_ after I boot the time is missing from the top bar, right side :?

Is there a Terminal command that will get the time to show :?: (*so I don't have to reboot*)

---

### Post by howefield on 2013-10-31
Usually,

```
killall unity-panel-service
```

will do it.

---

### Post by vanadium on 2013-11-01
Fix to this issue has been pushed today through the software updates.

---

### Post by Botruckle on 2013-11-17
It appeared after some updates were installed, but disappeared on the next reboot. Haven't seen it since. The various fixes I've read on forums haven't worked. The system settings, date and time also looks like a map of the world for time-zones, and has no check-boxes at all.

---

### Post by coffeecat on 2013-11-17
@Botruckle, try this. Open the window that has the map of the world, and then choose the Clock tab - the world map is on the Time & Date tab. In the clock tab, make sure the "Show a clock in the menu bar" box is ticked and check the other settings there.

---

### Post by Botruckle on 2013-11-18
Not sure what you mean by "tab". I click Applications, System Settings, then Date & Time. There is no Clock option in the list, and once Date & Time is opened, there are no tabs. If I click back to All Settings, there is still no option for Clock.

---

### Post by coffeecat on 2013-11-18
> **Botruckle said:**
> Not sure what you mean by "tab".

Exactly what is normally meant by a [tab in a GUI]("http://en.wikipedia.org/wiki/Tab_%28GUI%29"). You click on a tab and you get a different set of options. Have a look in the two screenshots. There are two tabs: "Time & Date" and "Clock". I have ringed them in red.

[ATTACH=CONFIG]247919[/ATTACH]   [ATTACH=CONFIG]247920[/ATTACH]

---

### Post by Botruckle on 2013-11-18
Ah. I have no Clock tab in mine (see pic).

[ATTACH=CONFIG]247927[/ATTACH]

---

### Post by vanadium on 2013-11-20
> **vanadium said:**
> Fix to this issue has been pushed today through the software updates.

It is clear that the updates to this day did not fix the issue. Now and then, it still happens that the datetime indicator is not there. The bug is open since 20 september ([https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1228360](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1228360))

---

### Post by Botruckle on 2013-11-23
The software updates rolled out a day or two ago brought the time and date back, though there is still no clock tab on my System Settings, Date and Time.

---

### Post by vanadium on 2013-11-24
> **Botruckle said:**
> The software updates rolled out a day or two ago brought the time and date back, though there is still no clock tab on my System Settings, Date and Time.

The issue is random. Sometimes, but not always, the clock indicator is not there after startup. It must be a problem with the startup routines.

---

### Post by Ertai87 on 2013-12-02
This issue just happened to me for the first time.  Some details, since my problem is a bit different from OP:

Clock has appeared regularly up until now, with no problems; this is the first time it's happened as far as I'm aware.

The killall suggestion earlier in the thread does not work.

Under "clock" in settings, the entire page is greyed out, but the option "add clock to menu bar" is checked.

I'll try rebooting and seeing if that helps, just adding another voice to this problem.  Thanks.

EDIT: Clock is back on reboot.

---

### Post by HC48 on 2014-05-22
This (*Under "clock" in settings, the entire page is greyed out, but the option "add clock to menu bar" is checked*.)
 just happened to me too. Rebooted and AOK, thanks Ertai87

---

