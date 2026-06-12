---
title: "Gutsy on HP Laptop: Battery Meter GONE!"
date: 2007-10-23
forum: General Help
---

### Post by phibit on 2007-10-23
My battery meter on my HPdv2120ca laptop used to work great with Feisty, but now when I start up Gutsy the battery meter is absent. I find that odd, considering gnome-power-manager is loaded and running. 

I tried launching kpowersave, but that little tray icon just displays it as "plugged in" ALL THE TIME, so it's basically useless.

Anyone else have this problem/know a fix?

---

### Post by brk3 on 2007-10-23
Maybe if you try just the gnome power applet? Right click the panel and go add applet or something similar it should be in the list.

---

### Post by vespo on 2007-10-23
Hi

the default behavoir for gutsy is that the battery icon is shown only if it is any activity on it (chargin/dicharging). Be sure that you change the preferences to "always show an icon" if you want it there all the time

Cheers
vespo

---

### Post by phibit on 2007-10-23
I tried both of the suggestions above, and they worked in their own, original ways.

The gnome panel applet for battery level works, as it does display my battery level. However I was look for the complete power management tray applet, that allows cpu freq control and screen brightness control.

Modifying the settings of the gnome-power-management tool to display an icon tray also worked. The icon DISPLAYS, but the information it displays is WRONG... it always says it's plugged in.

Ideally I would like a combination of both these outcomes, in that the tray icon would accurately interface with the battery conditions.

Thanks for the suggestions though.

---

### Post by vespo on 2007-10-29
Have you tried to restart the acpi daemon to see if it helps at all (and a few plug/unplug of your power cord of course)?

```
sudo /etc/init.d/acpid restart
```

---

### Post by phibit on 2008-04-07
I have tried this but it doesn't work... This problem is still persistent :(

---

