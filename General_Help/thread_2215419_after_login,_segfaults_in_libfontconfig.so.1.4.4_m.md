---
title: "after login, segfaults in libfontconfig.so.1.4.4 makes system unresponsive"
date: 2014-04-06
forum: General Help
---

### Post by skoraw on 2014-04-06
Hi, 

My system, 64-bit, ubuntu 12.04, all of the packages were updated as of yesterday, 3.5.0-48-generic becomes unresponsive immediately after I login and enter my password. 

I checked my syslog and found several several segfaults from libfontconfig. The complete syslog is at: [http://cl.ly/3I3x0J3d2J30](http://cl.ly/3I3x0J3d2J30)

Here the segfaults that I found: 
```
pr  6 14:40:21 thenameofmysystem kernel: [   59.676848] gnome-settings-[2046]: segfault at 4 ip 00007f21f121ec80 sp 00007fff0bc7ad90 error 4 in libfontconfig.so.1.4.4[7f21f1214000+34000]
Apr  6 14:40:22 thenameofmysystem gnome-session[1998]: WARNING: Application 'gnome-settings-daemon.desktop' killed by signal
Apr  6 14:40:43 thenameofmysystem dbus[942]: [system] Activating service name='org.freedesktop.UDisks' (using servicehelper)
Apr  6 14:40:43 thenameofmysystem dbus[942]: [system] Successfully activated service 'org.freedesktop.UDisks'
Apr  6 14:40:43 thenameofmysystem kernel: [   81.776886] ISO 9660 Extensions: Microsoft Joliet Level 3
Apr  6 14:40:43 thenameofmysystem kernel: [   81.833289] ISO 9660 Extensions: RRIP_1991A
Apr  6 14:40:45 thenameofmysystem kernel: [   83.498700] nm-applet[2095]: segfault at 4 ip 00007fa609b4ec80 sp 00007fff474e2890 error 4 in libfontconfig.so.1.4.4[7fa609b44000+34000]
Apr  6 14:40:47 thenameofmysystem kernel: [   85.948435] alarm-clock-app[2084]: segfault at 4 ip 00007f8f42af6c80 sp 00007fffc011c680 error 4 in libfontconfig.so.1.4.4[7f8f42aec000+34000]
Apr  6 14:40:49 thenameofmysystem kernel: [   87.980684] nautilus[2093]: segfault at 4 ip 00007f5e340e0c80 sp 00007fffc02003a0 error 4 in libfontconfig.so.1.4.4[7f5e340d6000+34000]
Apr  6 14:40:50 thenameofmysystem kernel: [   88.266507] compiz[2079]: segfault at 4 ip 00007f39ffd31c80 sp 00007fff1c5803d0 error 4 in libfontconfig.so.1.4.4[7f39ffd27000+34000]
```

At this point, I am a bit confused for how to continue troubleshootign this. 
Any help would be appreciated.

---

