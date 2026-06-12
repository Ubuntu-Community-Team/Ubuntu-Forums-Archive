---
title: "Problems with installing KClock"
date: 2024-01-11
forum: General Help
---

### Post by Princey on 2024-01-11
Hi folks. I'm currently running Kubuntu 22.04. I've been trying to install kclock otherwise known as 'clock' from invent.kde.org. Truth is I've tried the one in Discover (uses snap) and the flatpak version and both result in the same issues. The alarm and timers section doesn't work. Gives me an error message stating that the daemon kclockd was not found. So I tried building it from the code on github as I noticed that among the scripts and files provided, the kclockd daemon was present as part of the source code. But, I'm stock on the ```
make
``` part as I'm thrown an error message with regards to cmake. > CMake Error at CMakeLists.txt:22 (find_package):
  Could not find a configuration file for package "ECM" that is compatible
  with requested version "5.240.0".

  The following configuration files were considered but not accepted:

    /usr/share/ECM/cmake/ECMConfig.cmake, version: 5.92.0.

Any ideas where I go from there or is there a way to install the kclockd daemon from the repositories?

---

### Post by SeijiSensei on 2024-01-11
I'm not sure what kclock is. The only clocks I've used are the ones that run as widgets. There's both an analog and digital clock widget available if you right-click on the Desktop and choose "Add Widgets." Don't know about support for alarms and timers. I use my phone for things like that.

---

### Post by Princey on 2024-01-11
I'm aware of these and I do have that option. The reason I wanted to use kclock was for the alarm and stop watch features. The ones via widgets don't have that functionality.

---

### Post by Princey on 2024-01-15
Ok....sorry to bump this guys, but I sure do need help with those who're more adept at programming. Here is where I think the issue lies...the CMakeLists.txt supplied by the developer of the app has the following lines > set(QT_MIN_VERSION "6.5.0"), however, the QT version that comes with 22.04 is 5.15.3. I'm wondering if that could be one of the issues that have me stuck.

---

### Post by norobro on 2024-01-15
The "release/23.04" branch has Qt 5.15.2 as the minimum version required: [https://github.com/KDE/kclock/blob/release/23.04/CMakeLists.txt#L20](https://github.com/KDE/kclock/blob/release/23.04/CMakeLists.txt#L20)

---

### Post by #&amp;thj^% on 2024-01-15
I'm not sure why your flatpak (Clock) isn't working, but mine work flawlessly.
Permissions possibly?
EDIT for mine:
```
flatpak permission-show org.kde.kclock 
Table         Object       App            Permissions Data
notifications notification org.kde.kclock yes         0x00
#### AND
flatpak info --show-permissions org.kde.kclock 
[Context]
shared=network;ipc;
sockets=x11;wayland;pulseaudio;fallback-x11;
devices=dri;
filesystems=xdg-config/gtk-3.0:ro;xdg-config/kdeglobals:ro;

[Session Bus Policy]
com.canonical.AppMenu.Registrar=talk
org.kde.kconfig.notify=talk
org.kde.KGlobalSettings=talk
org.kde.kclockd=own
org.freedesktop.Notifications=talk
org.kde.Solid.PowerManagement=talk

```

---

### Post by Princey on 2024-01-17
Thanks. I finally found out why my flatpak wasn't working. I had just went ahead and installed the flatpak version without setting up flatpak environment first. Once I did that, it worked fine. Thanks for the insight. This can be marked as "solved".

---

### Post by MAFoElffen on 2024-01-17
We mark our own thread as "Solved"... (The person who started it.)

Please select the "Thread Tools" link in the upper right > Then select "Solved".

---

