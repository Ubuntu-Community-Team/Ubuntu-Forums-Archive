---
title: "No systray icon in Amarok under GNOME"
date: 2006-11-05
forum: General Help
---

### Post by DownloadTHIS on 2006-11-05
Is there any way to get the system tray icon to show up from KDE apps in GNOME?

---

### Post by harty83 on 2006-11-05
They should just show up.

Are you sure it is running?

I just tried to install amarok under gnome and when I try to open it, I get:

```
alan@hartyslaptop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

Anyone know why amarok is not opening?  On my desktop with edgy gnome it opens fine.

---

### Post by harty83 on 2006-11-05
Figured out my problem...bad config file.  All works fine now.

---

### Post by DownloadTHIS on 2006-11-05
The program is running, and it leaves a space where the icon should be, but there's no icon.

---

### Post by Lucas2005 on 2006-11-21
I had the same problem, Amarok will run but when i mimized it or even closed it down, it would not show an icon on the "system tray".  I would have to run the program again.  The option to show the icon in the tray was checked.

I went into "System Monitor" and ended the "amarokapp" process and re-launched the program... now it is fixed  :)

---

### Post by darundal on 2007-10-29
Using Gutsy, Amarok just randomly decided that it's tray icon should be running in a separate window (it doesn't appear in the tray, it appears in a small window the size of the icon). I have tried setting it to use the tray icon (at which point it appears in a window) or not (at which point the window with the tray icon disappears). Aqualung also displays the same behavior.

---

