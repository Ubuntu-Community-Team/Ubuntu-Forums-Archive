---
title: "Internal Error with HAL!, Errors with dbus in Banshee and Update Manager."
date: 2007-07-25
forum: General Help
---

### Post by mister harbies on 2007-07-25
Hi guys,

All this happened in one night to narrow it down. Not sure if it was something I installed. Have been trying to get some sort of notification system working on my Ubuntu desktop, and had tried a few projects.

I must have mucked something up to cause these problems, or I mucked up a whole lot of things and caused lots of isolated problems? Can anyone help out here?

Is the HAL error related to the dbus installation? I installed a banshee extension for the dbus, which might explain the error with banshee. The environment is not properly set up? Wants me to fix my environment or run banshee through dbus-launch. Unable to open the system message bus. 

Update Manager (the notification with the white star in an orange box) reported that it couldn't install some updates due to an error in the dbus script? I tried it again, and now it works? All is fine there.

I thought I would restart my computer. But the HAL! internal error is still there. And Banshee still reports that dbus is not available.

I do see the dbus-daemon and dbus-launch running in the system processes.

Cheers,

---

### Post by mister harbies on 2007-07-29
Bump

---

### Post by postalservice14 on 2007-10-11
Anyone got this figured out?  I am having the same problem...

Thanks,

John

---

### Post by pangalactic on 2007-11-09
Try running banshee from a command line, invoking it through dbus-launch.

:~$ dbus-launch banshee &

If that works, modify the launch icon to match.

Pang

---

