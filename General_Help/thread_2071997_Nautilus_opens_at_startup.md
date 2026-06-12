---
title: "Nautilus opens at startup"
date: 2012-10-16
forum: General Help
---

### Post by oygle on 2012-10-16
Each time I boot, Nautilus runs and opens at 'home', yet there doesn't appear to be anything defined under Startup, under System Settings.

There is only one bash script defined, and that is gtk2-default-theme.rc.sh

That script is in /usr/share/kubuntu-default-settings, and the contents are

```

#!/bin/bash

# Make sure our customised gtkrc file is loaded.
export GTK2_RC_FILES=$HOME/.gtkrc-2.0-kde4

```

Oygle

---

### Post by oygle on 2012-10-16
In /etc/xdg/nautilus-autostart.destop ..

```

[Desktop Entry]
Type=Application
Name=Files
Exec=nautilus -n
OnlyShowIn=GNOME;Unity;
AutostartCondition=GSettings org.gnome.desktop.background show-desktop-icons
NoDisplay=false
X-Ubuntu-Gettext-Domain=nautilus

```

So, I assume there is a 'bug' there, because the code says "OnlyShowIn=GNOME;Unity;" , and I'm running Kubuntu, not Unity.

Oygle

---

### Post by Bucky Ball on 2012-10-16
Sure you didn't just shutdown machine with Nautilus open and the 'Save Session' box clicked?

Go for a shutdown/restart and see if that box is clicked. If so, cancel reboot, close everything (including Nautilus) then go for shutdown, make sure the box *is* ticked and restart. 

The machine should restart with a blank slate.

What release are you using?

---

### Post by oygle on 2012-10-16
> **Bucky Ball said:**
> Sure you didn't just shutdown machine with Nautilus open and the 'Save Session' box clicked?

Yes, I'm 100% sure, as I don't use Nautilus (use Dolphin), and I always close all windows before a shutdown/restart.[/quote]

> **Bucky Ball said:**
> Go for a shutdown/restart and see if that box is clicked. If so, cancel reboot, close everything (including Nautilus) then go for shutdown, make sure the box *is* ticked and restart.

The box isn't clicked on shutdown/restart.

> **Bucky Ball said:**
> What release are you using?

Ubuntu 12.04, with Kubuntu desktop installed.

Thanks,

Oygle

---

### Post by oygle on 2012-11-01
Anyone ??

---

### Post by oygle on 2013-04-30
Does anyone know how to fix this please ?

---

