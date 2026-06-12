---
title: "Ubuntu 24.04: QSystemTrayIcon disappears after logout/login"
date: 2024-05-03
forum: General Help
---

### Post by anshah on 2024-05-03
Running a Qt UI application on Ubuntu 24.04. Upon initial install the system tray icon is visible. However, after relogin or reboot the system tray icon disappears. 

The Qt application uses QSystemTrayIcon:
```
QSystemTrayIcon *trayIcon = new QSystemTrayIcon(this);
QIcon icon(trayImage);
m_pTrayIcon->setIcon(icon);
m_pTrayIcon->show();

```
On previous Ubuntu versions, this was fixed by installing the Gnome Shell Extension [COLOR=#ff0000]*gnome-shell-extension-appindicator*[/COLOR]. However, on 24.04 this did not seem to make a difference.

Few questions:


[LIST]
[*]I know the windowing system changed to Wayland for 24.04 whereas it was X11 previously. This may have affected the system tray icon behavior because the App Indicator Gnome Shell Extension was developed for X11 and is not maintained.
[*]I feel like I encounter a new system tray icon issue every Ubuntu release as the behavior changes. What are the alternatives to this? My application is based in Qt so do not have any other choice but QSystemTrayIcon just seeing if there is any other tool out there because a bit frustrated at the moment.
[/LIST]

---

### Post by coffeecat on 2024-05-03
Duplicate of [https://ubuntuforums.org/showthread.php?t=2497419](https://ubuntuforums.org/showthread.php?t=2497419)

Thread closed.

---

