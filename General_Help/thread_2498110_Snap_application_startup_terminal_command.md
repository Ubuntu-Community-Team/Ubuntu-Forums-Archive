---
title: "Snap application startup terminal command"
date: 2024-05-30
forum: General Help
---

### Post by faust99 on 2024-05-30
How does one work out the terminal command to an application installed via snap? Specifically, I need to know the command to start nextcloud-desktop-client from the terminal.

---

### Post by Rubi1200 on 2024-05-31
What does
```
snap list
``` show?

You should be able to run it with either of these two commands:
```
nextcloud-client

snap run nextcloud-client

```

---

### Post by ActionParsnip on 2024-05-31
You can use TAB to autocomplete stuff, so type a few characters you think start the command, then press the TAB key a few times. It may show up

---

### Post by faust99 on 2024-05-31
snap list shows 'nextcloud-desktop-client', but running 'snap run nextcloud-desktop-client' results in error: cannot find app "nextcloud-desktop-client" in "nextcloud-desktop-client"

---

### Post by faust99 on 2024-05-31
Thank you - I've been starting it from the Activities Overview. I'd like to add it to my startup applications, which is why I need the terminal command.

---

### Post by deadflowr on 2024-05-31
For fun I looked at this
You can find the snap .desktop files in the /var/lib/snapd/desktop/applications folder
try 
```
cp /var/lib/snapd/desktop/applications/nextcloud-desktop-client_nextcloud.desktop ~/.config/autostart
```
This will put the desktop file in the autostart directory.
Should set it to launch at login.
Should also show in Startup Applications too.

sidenote
FWIW, If you want, the executing commands for all snaps are located in /snap/bin.
more or less

---

### Post by faust99 on 2024-05-31
Thank you kindly, on both counts.

> **deadflowr said:**
> For fun I looked at this
You can find the snap .desktop files in the /var/lib/snapd/desktop/applications folder
try 
```
cp /var/lib/snapd/desktop/applications/nextcloud-desktop-client_nextcloud.desktop ~/.config/autostart
```
This will put the desktop file in the autostart directory.
Should set it to launch at login.
Should also show in Startup Applications too.

sidenote
FWIW, If you want, the executing commands for all snaps are located in /snap/bin.
more or less

---

