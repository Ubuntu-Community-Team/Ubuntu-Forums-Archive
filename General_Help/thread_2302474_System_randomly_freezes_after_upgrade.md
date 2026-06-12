---
title: "System randomly freezes after upgrade"
date: 2015-11-10
forum: General Help
---

### Post by madmetal on 2015-11-10
I upgraded from 15.04 to 15.10 and now the system randomly freezes. Randomly means that it freezes after 3 minutes or after 5 hours of use. 
I checked /var/log/syslog and i found these errors happening before i had to hard shut it off. 

```
Nov 11 00:27:54 Ubuntu-spyros gnome-session[2442]: ** (zeitgeist-datahub:3208): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, manifestation and actor are required
Nov 11 00:27:54 Ubuntu-spyros gnome-session[2442]: [2015-11-10T22:27:54] [ERR] hddtemp: failed to open connection.
Nov 11 00:27:54 Ubuntu-spyros gnome-session[2442]: [2015-11-10T22:27:54] [ERR] atasmart: sk_disk_open() failure: /dev/sda.
Nov 11 00:27:54 Ubuntu-spyros gnome-session[2442]: [2015-11-10T22:27:54] [ERR] nvctrl: Failed to retrieve NVIDIA information.
Nov 11 00:27:59 Ubuntu-spyros dbus[1897]: [system] Activating service name='com.ubuntu.IndicatorCpufreqSelector' (using servicehelper)
```

Just removed hddtemp, cpufreqindicator and will see. 
Any other facing freezing problems after upgrade?

---

### Post by madmetal on 2015-11-11
Nothing changed. Still freezing randomly, more often when watching html5 videos/playing games. 
Laptop is an Asus F751M. Didn't not have any freeze problems in 15.04, thinking of degrading :/

> Nov 11 21:10:08 Ubuntu-spyros gnome-session[2135]: (nm-applet:2296): nm-applet-WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries
Nov 11 21:10:09 Ubuntu-spyros obexd[2490]: OBEX daemon 5.35
Nov 11 21:10:14 Ubuntu-spyros org.gnome.zeitgeist.Engine[2041]: ** (zeitgeist-datahub:2521): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Nov 11 21:10:23 Ubuntu-spyros gnome-session[2135]: ** (zeitgeist-datahub:2506): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, manifestation and actor are required
Nov 11 21:10:24 Ubuntu-spyros gnome-session[2135]: [2015-11-11T19:10:24] [ERR] hddtemp: failed to open connection.
Nov 11 21:10:24 Ubuntu-spyros gnome-session[2135]: [2015-11-11T19:10:24] [ERR] atasmart: sk_disk_open() failure: /dev/sda.
Nov 11 21:10:24 Ubuntu-spyros gnome-session[2135]: [2015-11-11T19:10:24] [ERR] nvctrl: Failed to retrieve NVIDIA information.

---

