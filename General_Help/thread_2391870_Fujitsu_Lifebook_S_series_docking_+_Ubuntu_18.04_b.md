---
title: "Fujitsu Lifebook S series docking + Ubuntu 18.04 boot (Login Hangs)"
date: 2018-05-14
forum: General Help
---

### Post by prabhakaran1989 on 2018-05-14
I recently upgraded to Ubuntu 18,04 from 16.04. 

The first big problem I noticed is the following:

**Problem:**
- If I have docked my laptop to a docking station (connected to two external monitors) then the system hangs before the login page appears.
  - I can't use Alt+Shift+F1 (to get a Terminal) or do anything to restart the x server or something..

**Current Solution**
- I have to start my laptop not connecting to the docking station
- Login with any available GUI such as gnome, unity, etc.
- Then attach the docking station, then everything works. I can connect two monitors and use them without any problem.


While I am connected to the docking station, if I restart or logout , then the problem appears. I have to force shutdown my laptop to boot again. 

How do I really narrow down the problem?

---

### Post by mastablasta on 2018-05-15
logs in /var/log or in a log viewer

check for any errors, or places where the boot stops. 

what doe sit mean that the system hangs? is there any error message? or just blank screen? what happens if you unplug it from the dock at that time?

i use a Fujitsu at work (windows 10) and occasionally when i dock it get's blank screen, so i need to open the laptop before i could log in. sometimes though it would just go directly into hibernate. i have to say i am not impressed by the way they've made it. even on win10 it doesn't work as it should.

---

### Post by coffeecat on 2018-05-15
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by prabhakaran1989 on 2018-05-25
Hangs: 
- I meant blank screen (ubuntu default background colour) with a mouse pointer, and the mouse pointer is not responsive to mouse activities. 
- Alt+Shift+F1: not working
- Undocking does not change anything

I have to force reboot. 

I tried looking at syslog file, here are some of the errors:

Current kernel version:
```

Linux xxx 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

Errors that could cause the problem.

```

May 25 11:46:07 xxx gnome-session[1161]: gnome-session-binary[1161]: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.ScreenSaver exited with status 1
May 25 11:46:07 xxx gnome-session-binary[1161]: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.ScreenSaver exited with status 1
May 25 11:46:11 xxx gnome-session[1161]: gnome-session-binary[1161]: WARNING: App 'spice-vdagent.desktop' exited with code 1
May 25 11:46:11 xxx gnome-session-binary[1161]: WARNING: App 'spice-vdagent.desktop' exited with code 1
May 25 11:46:11 xxx gnome-shell[1205]: Error looking up permission: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.impl.portal.PermissionStore was not provided by any .service files
May 25 11:46:12 xxx gnome-shell[1205]: JS WARNING: [resource:///org/gnome/shell/ui/windowManager.js 1468]: reference to undefined property "MetaWindowXwayland"
May 25 11:46:56 xxx kernel: [   54.411587] usb 1-1.6.1.4: 1:1: usb_set_interface failed (-19)
May 25 11:46:56 xxx kernel: [   54.411939] usb 1-1.6.1.4: 1:1: usb_set_interface failed (-19

```


The complete Syslog (reboot) is here: [https://pastebin.com/NKek4Ev2](https://pastebin.com/NKek4Ev2)

---

