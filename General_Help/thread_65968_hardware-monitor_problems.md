---
title: "hardware-monitor problems"
date: 2005-09-15
forum: General Help
---

### Post by HanKoo on 2005-09-15
I installed hardware-monitor 1.2-1.1ubuntu1 with synaptic. Some problems:
"gnome panel encountered problems while loading OAFIID:HardwareMonitor".
There seems to be a patch for ubuntu in
[http://packages.qa.debian.org/h/hardware-monitor.html](http://packages.qa.debian.org/h/hardware-monitor.html)
so I tried first to compile an unpatched version from
apt-get source hardware-monitor.

However, I encountered another problem when doing ./configure
i was told that libgnomeuimm-2.6 (and some other libs) were missing.
This is not true, they have been installed with synaptic. 
What is missing is the file /usr/lib/pkg-config/libgnomeuimm-2.6.pc and thus pkg-config could not find them.

I really can't figure out how package & library management is made from pkg-config point of view?
Should there exist a corresponding .pc file for each library to be used with pkg-config? Should i build this by myself? How, if so? Or do i just have a badly built configure

---

