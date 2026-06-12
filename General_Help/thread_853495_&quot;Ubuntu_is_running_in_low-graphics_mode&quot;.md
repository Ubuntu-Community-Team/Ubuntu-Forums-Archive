---
title: "&quot;Ubuntu is running in low-graphics mode&quot; after upgrade"
date: 2008-07-08
forum: General Help
---

### Post by billmcn on 2008-07-08
I had a working version of Ubuntu about a year ago.  Sometime in the past few months, I upgraded to the latest version and now when I boot I get a message box titled "Ubuntu is running in low-graphics mode".  It gives me an option to manually select my monitor and video card, but I haven't found a combination that works so I'm making do with 800x600 resolution.

I am currently running Hardy, 8.04.  This is on a MacBook inside Parallels Desktop 3.0.  According to the Mac System profiler I have an "Intel GMA 950" video card and a 1280x800 Color LDC display.

I've seen similar posts in this forum about problems with Nvidia drivers, but I don't have an Nvidia driver so I think it's a separate issue.

How do I go about debugging this?  Thanks.

---

### Post by sayakb on 2008-07-08
Open a terminal and type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And restart X to see if it works.

---

### Post by billmcn on 2008-07-08
Running that command produced the following error:


```
$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for billmcn:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080708144258
FATAL: Error inserting battery (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/battery.ko): No such device

```

Also, how do you restart X?  Is that Ctrl-Alt-Backspace?

---

### Post by billmcn on 2008-07-08
After restarting the system, I don't get the message box and the resolution is fine again.  This appears to be fixed.  Thanks.

---

