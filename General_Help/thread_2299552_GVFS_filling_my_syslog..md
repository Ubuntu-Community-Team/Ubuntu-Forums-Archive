---
title: "GVFS filling my syslog."
date: 2015-10-19
forum: General Help
---

### Post by welefort on 2015-10-19
Running Ubuntu 15.10.

I found these two lines keep appearing in my syslog every 2 seconds or so.   I do have an encrypted filesystem,  so Im not sure if thats related.  

```
Oct 19 06:27:09 wally org.gnome.panel.applet.MultiLoadAppletFactory[1911]: glibtop: statvfs '/root/.gvfs' failed: Permission denied
Oct 19 06:27:09 wally org.gnome.panel.applet.MultiLoadAppletFactory[1911]: glibtop: statvfs '/run/user/1001/gvfs' failed: Permission denied
```

---

### Post by ian-weisser on 2015-10-20
glibtop is a cpu monitor. Do you have a CPU monitor installed?

---

### Post by welefort on 2015-10-21
I dont have any extra one installed,  but I do have the system monitor running in my top bar.  I have 3 windows.   1 for processor,  1 for disk and 1 for network.

---

### Post by arumbold on 2015-12-22
Hi,

The logs are caused by the disk activity monitor in the system monitor applet.

It tries to observe disk activity for multiple users, not just yourself. You can see in your log that the monitor is trying to stat gvfs for the root user, and also for user with id 1001.

'/root/.gvfs' failed: Permission denied
'/run/user/1001/gvfs' failed: Permission denied

You can see on my system I also get the same issue, running the MATE panel and applet for user 42 (gdm):

Dec 22 11:02:50 <hostname> org.mate.panel.applet.MultiLoadAppletFactory[2483]: glibtop(c=5008): [WARNING] statvfs '/run/user/42/gvfs' failed: Permission denied

---

