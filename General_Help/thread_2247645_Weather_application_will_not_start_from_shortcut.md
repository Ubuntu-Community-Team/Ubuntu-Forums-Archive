---
title: "Weather application will not start from shortcut"
date: 2014-10-09
forum: General Help
---

### Post by OriTheEep on 2014-10-09
Ubuntu 14.04 / Gnome Flashback Metacity

Curious thing: the application "gnome-weather 3.10.1-0ubuntu1" runs perfectly well if started from the Applications menu but any attempt to start from a shortcut or as a Startup Application fails.

The command that appears in the shortcut created by dragging the Applications menu item to the desktop is:[INDENT]/usr/share/org.gnome.Weather.Application/org.gnome.Weather.Application
[/INDENT]

Running this in a terminal gives:[INDENT]xxx@Xxxxxxx:~$ /usr/share/org.gnome.Weather.Application/org.gnome.Weather.Application
GWeather-Message: Failed to get Yr.no forecast data: 404 Not Found

GWeather-Message: Failed to get Yr.no forecast data: 404 Not Found


(org.gnome.Weather.Application:2440): Gjs-CRITICAL **: Attempting to call back into JSAPI during the sweeping phase of GC. This is most likely caused by not destroying a Clutter actor or Gtk+ widget with ::destroy signals connected, but can also be caused by using the destroy() or dispose() vfuncs. Because it would crash the application, it has been blocked and the JS callback not invoked.
[/INDENT]


I rather wish I did understand all that.

This is more of a niggle than a serious complaint but searching the web with the error message only gave two hits, neither of which looked relevant. The problem occurs on three machines that I know of, running this Ubuntu / Gnome combination.

Any ideas?

---

