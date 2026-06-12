---
title: "Why Does My Snap Store App Look Like This?"
date: 2022-04-28
forum: General Help
---

### Post by Mark76 on 2022-04-28
[ATTACH=CONFIG]290353[/ATTACH][ATTACH=CONFIG]290354[/ATTACH]

What am I missing? :confused:

---

### Post by TenPlus1 on 2022-04-30
Snap store had issues with local theming and icon sets, which is why I recommend installing gnome-software as a backup until it's sorted.

---

### Post by Mark76 on 2022-05-06
Same thing happens on Gnome-Software.   My DE is Xfce4.16 on Ubuntu 22.04

---

### Post by #&amp;thj^% on 2022-05-06
I use a very old script that i modified from 20.04 when it happened there as well.
I put it in auto-start
```
#!/bin/sh
if [ ! -d /snap/overlay ]; then
 exit 1
fi

GNOMEDIR=`echo /snap/gnome-3-*`

if [ -z "$GNOMEDIR" ]; then
  exit 1
fi

for ff in $GNOMEDIR; do

  GNOMEVER=`readlink $ff/current`

  if [ -z "$GNOMEVER" ]; then
    exit 1
  fi

  /snap/overlay/current/overlay $ff/$GNOMEVER
  cp -rp "/usr/share/themes/My Theme" $ff/$GNOMEVER/usr/share/themes
  rm "$ff/$GNOMEVER/usr/share/themes/My Theme/gtk-3.0/assets"
  ln -s /snap/gtk-common-themes/current/share/themes/Ambiance/gtk-3.0/assets "$ff/$GNOMEVER/usr/share/themes/My Theme/gtk-3.0"
```
The app "overlay" is installed through snap.

---

