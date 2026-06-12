---
title: "Annoying Popup"
date: 2021-06-30
forum: General Help
---

### Post by gus_zernial on 2021-06-30
Ubuntu 20.04 with KDE Plasma desktop. I repeatedly get a popup asking me to login to mail.google.com. I do so, but my login is rejected. In fact, I'm already using Google mail in my Chromium browser, and I am logged in to same. What to do ????                  Gus

---

### Post by ActionParsnip on 2021-06-30
Do you have any plasmoids enabled that use gmail etc?

---

### Post by gus_zernial on 2021-07-15
I don't think so - below is a list of my plasmoids:

```
ls -rR ~/. local/share/plasma/

~/.local/share/plasma$ ls -rR
.:
look-and-feel  desktoptheme

./look-and-feel:
Mountain-landscapes-04  Aritim-Light  Aritim-Dark  Ant-Dark

./look-and-feel/Mountain-landscapes-04:
metadata.desktop  contents

./look-and-feel/Mountain-landscapes-04/contents:
splash  previews

./look-and-feel/Mountain-landscapes-04/contents/splash:
Splash.qml  images

./look-and-feel/Mountain-landscapes-04/contents/splash/images:
Mountain-landscapes-04.png  739.svg

./look-and-feel/Mountain-landscapes-04/contents/previews:
splash.png

./look-and-feel/Aritim-Light:
README.md  metadata.desktop  LICENSE  contents

./look-and-feel/Aritim-Light/contents:
previews  defaults

./look-and-feel/Aritim-Light/contents/previews:
preview.png  fullscreenpreview.jpg

./look-and-feel/Aritim-Dark:
README.md  metadata.desktop  LICENSE  contents

./look-and-feel/Aritim-Dark/contents:
previews  defaults

./look-and-feel/Aritim-Dark/contents/previews:
preview.png  fullscreenpreview.jpg

./look-and-feel/Ant-Dark:
metadata.desktop  contents

./look-and-feel/Ant-Dark/contents:
splash  previews  osd  logout  lockscreen  defaults  components

./look-and-feel/Ant-Dark/contents/splash:
Splash.qml  images

./look-and-feel/Ant-Dark/contents/splash/images:
logo.png  busy02.svg

./look-and-feel/Ant-Dark/contents/previews:
splash.png  preview.png  fullscreenpreview.jpg

./look-and-feel/Ant-Dark/contents/osd:
Osd.qml  OsdItem.qml

./look-and-feel/Ant-Dark/contents/logout:
timer.js  Logout.qml  LogoutButton.qml

./look-and-feel/Ant-Dark/contents/lockscreen:
MediaControls.qml  MainBlock.qml  LockScreenUi.qml  LockScreen.qml  LockOsd.qml  config.xml  config.qml

./look-and-feel/Ant-Dark/contents/components:
WallpaperFader.qml   UserList.qml      SessionManagementScreen.qml  Clock.qml    artwork
VirtualKeyboard.qml  UserDelegate.qml  KeyboardLayoutButton.qml     Battery.qml  ActionButton.qml

./look-and-feel/Ant-Dark/contents/components/artwork:
shutdown_primary.svgz  restart_primary.svgz  README.txt  logout_primary.svgz

./desktoptheme:
Aritim-Light-Flat-Blur     Aritim-Dark-Rounded-Blur  Aritim-Dark-Flat-Blur
Aritim-Dark-Rounded-Solid  Aritim-Dark-Flat-Solid    Ant-Dark

./desktoptheme/Aritim-Light-Flat-Blur:
widgets  transparent  README.md  opaque  Notes.txt  metadata.desktop  LICENSE  dialogs  colors

./desktoptheme/Aritim-Light-Flat-Blur/widgets:
viewitem.svg  tooltip.svg  tasks.svg  panel-background.svg  checkmarks.svgz  button.svgz

./desktoptheme/Aritim-Light-Flat-Blur/transparent:
widgets  dialogs

./desktoptheme/Aritim-Light-Flat-Blur/transparent/widgets:

./desktoptheme/Aritim-Light-Flat-Blur/transparent/dialogs:
background.svg

./desktoptheme/Aritim-Light-Flat-Blur/opaque:
widgets  dialogs

./desktoptheme/Aritim-Light-Flat-Blur/opaque/widgets:

./desktoptheme/Aritim-Light-Flat-Blur/opaque/dialogs:
background.svg

./desktoptheme/Aritim-Light-Flat-Blur/dialogs:
background.svg

./desktoptheme/Aritim-Dark-Rounded-Solid:
widgets  README.md  opaque  Notes.txt  metadata.desktop  LICENSE  dialogs  colors

./desktoptheme/Aritim-Dark-Rounded-Solid/widgets:
viewitem.svg  tooltip.svg  tasks.svg  panel-background.svg  checkmarks.svgz  button.svgz

./desktoptheme/Aritim-Dark-Rounded-Solid/opaque:
widgets  dialogs

./desktoptheme/Aritim-Dark-Rounded-Solid/opaque/widgets:

./desktoptheme/Aritim-Dark-Rounded-Solid/opaque/dialogs:
background.svg

./desktoptheme/Aritim-Dark-Rounded-Solid/dialogs:
background.svg

./desktoptheme/Aritim-Dark-Rounded-Blur:
widgets  transparent  README.md  opaque  Notes.txt  metadata.desktop  LICENSE  dialogs  colors

./desktoptheme/Aritim-Dark-Rounded-Blur/widgets:
viewitem.svg  tooltip.svg  tasks.svg  panel-background.svg  checkmarks.svgz  button.svgz

./desktoptheme/Aritim-Dark-Rounded-Blur/transparent:
widgets  dialogs

./desktoptheme/Aritim-Dark-Rounded-Blur/transparent/widgets:

./desktoptheme/Aritim-Dark-Rounded-Blur/transparent/dialogs:
background.svg

./desktoptheme/Aritim-Dark-Rounded-Blur/opaque:
widgets  dialogs

./desktoptheme/Aritim-Dark-Rounded-Blur/opaque/widgets:

./desktoptheme/Aritim-Dark-Rounded-Blur/opaque/dialogs:
background.svg

./desktoptheme/Aritim-Dark-Rounded-Blur/dialogs:
background.svg

./desktoptheme/Aritim-Dark-Flat-Solid:
widgets  weather  README.md  QRCode.jpg  metadata.desktop  LICENSE  dialogs  colors

./desktoptheme/Aritim-Dark-Flat-Solid/widgets:
viewitem.svgz      scrollbar.svgz         listitem.svgz              clock.svgz                 background.svgz
tooltip.svgz       plot-background.svgz   line.svgz                  checkmarks.svgz            arrows.svgz
toolbar.svgz       picker.svgz            lineedit.svgz              calendar.svgz              analog_meter.svgz
timer.svgz         panel-background.svgz  glowbar.svgz               button.svgz                action-overlays.svgz
tasks.svgz         pager.svgz             frame.svgz                 busywidget.svgz            actionbutton.svgz
tabbar.svgz        notes.svgz             dragger.svgz               branding.svgz
slider.svgz        monitor.svgz           containment-controls.svgz  bar_meter_vertical.svgz
scrollwidget.svgz  media-delegate.svgz    configuration-icons.svgz   bar_meter_horizontal.svgz

./desktoptheme/Aritim-Dark-Flat-Solid/weather:
wind-arrows.svgz

./desktoptheme/Aritim-Dark-Flat-Solid/LICENSE:
'CC BY-SA 4.0 EN.md'

./desktoptheme/Aritim-Dark-Flat-Solid/dialogs:
background.svgz

./desktoptheme/Aritim-Dark-Flat-Blur:
 widgets   README.md   Notes.txt   metadata.desktop  'LICENSE copy'   dialogs   colors

./desktoptheme/Aritim-Dark-Flat-Blur/widgets:
viewitem.svgz               scrollwidget.svgz      media-delegate.svgz        configuration-icons.svgz  bar_meter_horizontal.svgz
translucentbackground.svgz  scrollbar.svgz         listitem.svgz              clock.svgz                background.svgz
tooltip.svgz                plot-background.svgz   line.svgz                  checkmarks.svgz           arrows.svgz
toolbar.svgz                picker.svgz            lineedit.svgz              calendar.svgz             analog_meter.svgz
timer.svgz                  panel-background.svgz  glowbar.svgz               button.svgz               action-overlays.svgz
tasks.svgz                  pager.svgz             frame.svgz                 busywidget.svgz           actionbutton.svgz
tabbar.svgz                 notes.svgz             dragger.svgz               branding.svgz
slider.svgz                 monitor.svgz           containment-controls.svgz  bar_meter_vertical.svgz

./desktoptheme/Aritim-Dark-Flat-Blur/dialogs:
background.svgz

./desktoptheme/Ant-Dark:
widgets  metadata.desktop  icons  dialogs  colors

./desktoptheme/Ant-Dark/widgets:
viewitem.svgz               tabbar.svg            pager.svgz     containment-controls.svgz  bar_meter_horizontal.svgz
translucentbackground.svgz  slider.svgz           listitem.svgz  clock.svg                  background.svgz
tooltip.svgz                scrollwidget.svg      line.svgz      checkmarks.svg             arrows.svgz
toolbar.svgz                scrollbar.svg         lineedit.svg   button.svg                 action-overlays.svgz
timer.svgz                  plot-background.svgz  glowbar.svgz   busywidget.svgz            actionbutton.svg
tasks.svgz                  panel-background.svg  frame.svgz     bar_meter_vertical.svgz

./desktoptheme/Ant-Dark/icons:
system.svg  start.svg  audio.svg

./desktoptheme/Ant-Dark/dialogs:
_background.svgz  background.svg
```

---

### Post by gus_zernial on 2021-07-15
What I don't know how to do is to trace back to find what generates the popup. 

I note that the kde wallet is disabled on my system (by me in settings), but I still see these messages in /var/log/syslog:

```
dbus-daemon[1538]: [session uid=1000 pid=1538] Activating service name='org.kde.kwalletd5' requested by ':1.57' (uid=1000 pid=2133 comm="/opt/google/chrome/chrome --type=utility --utility" label="unconfined")
dbus-daemon[1538]: [session uid=1000 pid=1538] Successfully activated service 'org.kde.kwalletd5'
dbus-daemon[1538]: [session uid=1000 pid=1538] Activating service name='org.kde.kwalletd5' requested by ':1.57' (uid=1000 pid=2133 comm="/opt/google/chrome/chrome --type=utility --utility" label="unconfined")
dbus-daemon[1538]: [session uid=1000 pid=1538] Successfully activated service 'org.kde.kwalletd5'
```

---

### Post by gus_zernial on 2021-07-16
> **ActionParsnip said:**
> Do you have any plasmoids enabled that use gmail etc?

As I said above, I did not think I had any plasmoids that used gmail. But I was wrong.

In fact, I had inadvertently installed plasma-gmailfeed during an update of plasma-desktop, and that was the offending plasmoid that triggered the popups. After I removed plasma-gmailfeed - no more mail.gmail.com authentication popups. Problem solved.

It took me ever so long and so much google searching to discover the culprit. I hope this post may help others with this problem.

Gus

---

