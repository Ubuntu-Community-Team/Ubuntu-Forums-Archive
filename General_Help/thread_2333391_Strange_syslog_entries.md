---
title: "Strange syslog entries"
date: 2016-08-09
forum: General Help
---

### Post by pfeiffep on 2016-08-09
First off I haven't noticed visible failures on my system. 

Checking my syslog I found a few messages indicating some problem; these messages happened at the end of the boot up and haven't re-appeared since [5 hours later].
The weather applet displays the correct weather, the clock shows the correct time, cpu frequence display is normal. 
```

Aug  9 12:50:18 HP-T org.mate.panel.applet.MateWeatherAppletFactory[3994]: (mateweather-applet:4244): MateWeather-CRITICAL **: weather_info_get_icon_name: assertion 'info != NULL' failed
Aug  9 12:50:18 HP-T org.mate.panel.applet.MateWeatherAppletFactory[3994]: (mateweather-applet:4244): MateWeather-CRITICAL **: weather_info_get_temp_summary: assertion 'info != NULL' failed
Aug  9 12:50:18 HP-T org.mate.panel.applet.MateWeatherAppletFactory[3994]: (mateweather-applet:4244): MateWeather-CRITICAL **: weather_info_get_icon_name: assertion 'info != NULL' failed
Aug  9 12:50:18 HP-T dbus[2993]: [system] Activating service name='org.mate.SettingsDaemon.DateTimeMechanism' (using servicehelper)
Aug  9 12:50:18 HP-T dbus[2993]: [system] Successfully activated service 'org.mate.SettingsDaemon.DateTimeMechanism'
Aug  9 12:50:18 HP-T org.mate.panel.applet.MultiLoadAppletFactory[3994]: ** (mate-multiload-applet:4246): WARNING **: Failed to get pixmap 16777445,1106,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.ClockAppletFactory[3994]: ** (clock-applet:4242): WARNING **: Failed to get pixmap 16777445,835,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.CPUFreqAppletFactory[3994]: ** (mate-cpufreq-applet:4248): WARNING **: Failed to get pixmap 16777445,1178,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.MultiLoadAppletFactory[3994]: ** (mate-multiload-applet:4246): WARNING **: Failed to get pixmap 16777448,1106,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.CPUFreqAppletFactory[3994]: ** (mate-cpufreq-applet:4248): WARNING **: Failed to get pixmap 16777448,1178,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.ClockAppletFactory[3994]: ** (clock-applet:4242): WARNING **: Failed to get pixmap 16777448,835,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.ClockAppletFactory[3994]: ** (clock-applet:4242): WARNING **: Failed to get pixmap 16777469,835,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.ClockAppletFactory[3994]: ** (clock-applet:4242): WARNING **: Failed to get pixmap 16777472,835,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.CPUFreqAppletFactory[3994]: ** (mate-cpufreq-applet:4248): WARNING **: Failed to get pixmap 16777478,1178,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.ClockAppletFactory[3994]: ** (clock-applet:4242): WARNING **: Failed to get pixmap 16777475,835,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.MultiLoadAppletFactory[3994]: ** (mate-multiload-applet:4246): WARNING **: Failed to get pixmap 16777484,1106,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.ClockAppletFactory[3994]: ** (clock-applet:4242): WARNING **: Failed to get pixmap 16777478,835,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.MultiLoadAppletFactory[3994]: ** (mate-multiload-applet:4246): WARNING **: Failed to get pixmap 16777487,1106,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.ClockAppletFactory[3994]: ** (clock-applet:4242): WARNING **: Failed to get pixmap 16777481,835,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.ClockAppletFactory[3994]: ** (clock-applet:4242): WARNING **: Failed to get pixmap 16777484,835,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.ClockAppletFactory[3994]: ** (clock-applet:4242): WARNING **: Failed to get pixmap 16777487,835,0
Aug  9 12:50:18 HP-T org.mate.panel.applet.ClockAppletFactory[3994]: ** (clock-applet:4242): WARNING **: Failed to get pixmap 16777490,835,0
Aug  9 12:50:19 HP-T org.mate.panel.applet.MateWeatherAppletFactory[3994]: ** (mateweather-applet:4244): WARNING **: Failed to get pixmap 16777496,1007,0
Aug  9 12:50:19 HP-T org.mate.panel.applet.MateWeatherAppletFactory[3994]: ** (mateweather-applet:4244): WARNING **: Failed to get pixmap 16777499,1007,0
Aug  9 12:50:19 HP-T org.mate.panel.applet.MateWeatherAppletFactory[3994]: ** (mateweather-applet:4244): WARNING **: Failed to get pixmap 16777502,1007,0
Aug  9 12:50:19 HP-T org.mate.panel.applet.MateWeatherAppletFactory[3994]: ** (mateweather-applet:4244): WARNING **: Failed to get pixmap 16777523,1007,0
Aug  9 12:50:19 HP-T org.mate.panel.applet.MateWeatherAppletFactory[3994]: ** (mateweather-applet:4244): WARNING **: Failed to get pixmap 16777544,1007,0
Aug  9 12:50:20 HP-T org.gtk.vfs.Daemon[3994]: ** (process:4278): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
Aug  9 12:50:21 HP-T org.gtk.vfs.Daemon[3994]: ** (process:4278): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
```

Ubuntu MATE 16.04.1 standard install with one exception - I've deleted the lower panel and use Plank located on the bottom. Both Plank and upper panel are set to transparent.

I'm not certain where to investigate to attempt to remedy. This is a minor annoyance ... I haven't been stopped from doing anything on this machine

---

### Post by pfeiffep on 2016-08-11
Update
I installed a 'virgin' copy of Ubuntu MATE 16.04.1 in Virtual Box and discovered _* failed to get pixmap*_ errors are only present when panels are transparent.

---

