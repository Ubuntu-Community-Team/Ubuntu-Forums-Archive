---
title: "Switch to Xubuntu created ubuntu-mono icon theme issue"
date: 2018-02-23
forum: General Help
---

### Post by abe-stew on 2018-02-23
I recently moved from plain Ubuntu to Xubuntu via the apt install kubuntu-desktop method. Been pleasantly surprised at how much smoother KDE runs on my system compared to Gnome (including Gnome running X11 instead of Wayland). However, the only issue I have had is somehow my ubuntu-mono-dark icon theme has become messed up resulting in a range of issues on the machine. For example, a couple of applications refuse to open - likely due to not knowing how to resolve the icon theme issues. Running them from terminal gives the follow error:
```

Warning: Invalid Context= "stock" line for icon theme:  "/usr/share/icons/ubuntu-mono-dark/stock/16/" ((null):0, (null))

```

 If running specific applications (Clementine is one of them) pressing Alt+Tab will crash KDE so the taskbar, window decorations, etc all disappear. Running any python application that relies on Qt spews out the following errors:
```

Invalid Context= "stock" line for icon theme:  "/usr/share/icons/ubuntu-mono-dark/stock/16/"
Invalid Context= "stock" line for icon theme:  "/usr/share/icons/ubuntu-mono-dark/stock/22/"
Invalid Context= "stock" line for icon theme:  "/usr/share/icons/ubuntu-mono-dark/stock/24/"
Invalid Context= "stock" line for icon theme:  "/usr/share/icons/ubuntu-mono-dark/stock/32/"
Invalid Context= "stock" line for icon theme:  "/usr/share/icons/ubuntu-mono-dark/stock/48/"
Invalid Context= "stock" line for icon theme:  "/usr/share/icons/ubuntu-mono-dark/stock/64/"
Invalid Context= "stock" line for icon theme:  "/usr/share/icons/ubuntu-mono-dark/stock/128/"
```

When exploring Icons within the System Settings Module no example icons would display when selecting Ubuntu-Mono-Dark. Force reinstalling the package failed to resolve the issue. However, installing it via Get new Theme resulted in example icons being displayed when selected - but none of the other issues such as couple of applications not launching and KDE crashing when pressing Alt+Tab with specific applications open remain. Any ideas for what else I can try to fix this?

---

### Post by kerry_s on 2018-02-23
xubuntu uses xfce4 desktop not kde

kde desktop is kubuntu

---

### Post by abe-stew on 2018-02-24
Apologies - well spotted. Meant to say kubuntu. Managed to resolve apps not launching issue by removing the ubuntu-mono-dark inheritance from the papirus icon theme. However, it means I will need to do this every time the package updates so not the best long term solution. 

Also. using any task switchers that show a thumbnail of the application (breeze, breeze dark, thumbnail grid, etc) still crashes KDE.

---

