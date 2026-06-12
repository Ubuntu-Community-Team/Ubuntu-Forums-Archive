---
title: "Monitor blackout while attempting to switch workspaces"
date: 2023-01-30
forum: General Help
---

### Post by benjaminbreeg on 2023-01-30
[SIZE=2][FONT=trebuchet ms][COLOR=#24292F]Sometimes switching workspaces renders my two monitors blank for a few good seconds (10-15)[/COLOR], which is [COLOR=#24292F]extremely annoying. Reboot fixes it ... that is, until it starts happening again.[/COLOR]

[COLOR=#24292F]Here is what looks to me to be the relevant syslog chunk:[/COLOR]
```
[COLOR=#24292F]Jan 30 13:40:17 DadsLGGram kernel: [65484.743321] evdi: [I] (card2) Notifying display power state: on
Jan 30 13:40:17 DadsLGGram kernel: [65603.921376] evdi: [W] evdi_painter_connect:883 (card1) Double connect - replacing 000000004ef2fbbc with 000000004ef2fbbc
Jan 30 13:40:17 DadsLGGram kernel: [65603.921383] evdi: [I] (card1) Connected with Task 4896 (DesktopManagerE) of process 4851 (DisplayLinkMana)
Jan 30 13:40:17 DadsLGGram kernel: [65603.921386] evdi: [I] (card1) Connector state: connected
Jan 30 13:40:17 DadsLGGram kernel: [65603.954659] evdi: [I] (card1) Notifying mode changed: 3840x2160@60; bpp 32; pixel format XR24 little-endian (0x34325258)
Jan 30 13:40:17 DadsLGGram kernel: [65603.954664] evdi: [I] (card1) Notifying display power state: on
Jan 30 13:40:17 DadsLGGram kernel: [65603.961035] evdi: [I] (card2) Disconnected from Task 4896 (DesktopManagerE) of process 4851 (DisplayLinkMana)
Jan 30 13:40:17 DadsLGGram kernel: [65603.961041] evdi: [I] (card2) Removing i2c adapter bus number 16
Jan 30 13:40:17 DadsLGGram kernel: [65603.961318] evdi: [I] (card2) Closed by Task 4896 (DesktopManagerE) of process 4851 (DisplayLinkMana)
Jan 30 13:40:17 DadsLGGram gnome-shell[8763]: meta_display_get_monitor_in_fullscreen: assertion 'monitor >= 0 && monitor < n_logical_monitors' failed
Jan 30 13:40:17 DadsLGGram gnome-shell[8763]: meta_monitor_manager_get_logical_monitor_from_number: assertion '(unsigned int) number < g_list_length (manager->logical_monitors)' failed
Jan 30 13:40:17 DadsLGGram gnome-shell[8763]: meta_workspace_get_work_area_for_monitor: assertion 'logical_monitor != NULL' failed
Jan 30 13:40:17 DadsLGGram kernel: [65604.009533] evdi: [I] (card2) Opened by Task 4896 (DesktopManagerE) of process 4851 (DisplayLinkMana)
Jan 30 13:40:17 DadsLGGram kernel: [65604.010928] evdi: [I] (card2) Added i2c adapter bus number 16
Jan 30 13:40:17 DadsLGGram kernel: [65604.010932] evdi: [I] (card2) Connected with Task 4896 (DesktopManagerE) of process 4851 (DisplayLinkMana)
Jan 30 13:40:17 DadsLGGram kernel: [65604.010935] evdi: [I] (card2) Connector state: connected
Jan 30 13:40:17 DadsLGGram kernel: [65604.058600] evdi: [I] (card1) Notifying display power state: off
Jan 30 13:40:17 DadsLGGram kernel: [65604.058625] evdi: [I] (card1) Notifying display power state: on
Jan 30 13:40:17 DadsLGGram kernel: [65604.058753] evdi: [I] (card1) Notifying mode changed: 3840x2160@60; bpp 32; pixel format XR24 little-endian (0x34325258)
Jan 30 13:40:17 DadsLGGram kernel: [65604.058754] evdi: [I] (card1) Notifying display power state: on
Jan 30 13:40:17 DadsLGGram kernel: [65604.058793] evdi: [I] (card2) Notifying display power state: off
Jan 30 13:40:17 DadsLGGram kernel: [65604.058795] evdi: [I] (card2) Notifying display power state: off
Jan 30 13:40:17 DadsLGGram kernel: [65604.091989] evdi: [I] (card2) Connector state: connected
Jan 30 13:40:17 DadsLGGram kernel: [65604.092130] evdi: [I] (card2) Edid property set
Jan 30 13:40:17 DadsLGGram kernel: [65604.092268] evdi: [I] (card2) Connector state: connected
Jan 30 13:40:17 DadsLGGram gnome-shell[8763]: Timelines with detached actors are not supported. <dashtodockContainer>[<StBin>:0x561cd7d4e6c0] in animation of duration 500ms but not on stage.
Jan 30 13:40:17 DadsLGGram kernel: [65604.092398] evdi: [I] (card2) Edid property set
Jan 30 13:40:17 DadsLGGram kernel: [65604.362359] evdi: [I] (card1) Notifying display power state: off
Jan 30 13:40:17 DadsLGGram kernel: [65604.362386] evdi: [I] (card1) Notifying display power state: on
Jan 30 13:40:17 DadsLGGram kernel: [65604.362416] evdi: [I] (card1) Notifying mode changed: 3840x2160@60; bpp 32; pixel format XR24 little-endian (0x34325258)
Jan 30 13:40:17 DadsLGGram kernel: [65604.362417] evdi: [I] (card1) Notifying display power state: on
Jan 30 13:40:17 DadsLGGram kernel: [65604.362436] evdi: [I] (card2) Notifying display power state: on
Jan 30 13:40:17 DadsLGGram kernel: [65604.362438] evdi: [I] (card2) Notifying mode changed: 3840x2160@60; bpp 32; pixel format XR24 little-endian (0x34325258)
[/COLOR]
```[COLOR=#24292F]Ubuntu 22.10, kernel 6.1.6: [pastebin]("https://paste.ubuntu.com/p/Q2YDy5Qp7M/")
[Syslog pastebin]("https://paste.ubuntu.com/p/rTtxPf5NYz/")[/COLOR][/FONT][/SIZE]

---

### Post by benjaminbreeg on 2023-02-09
Here's more of the same:

```
Feb  9 12:12:49 DadsLGGram gsd-power[6900]: gsd_power_backlight_percentage_to_abs: assertion 'value <= 100' failed
Feb  9 12:13:49 DadsLGGram kernel: [47859.800736] evdi: [I] (card2) Notifying display power state: on
Feb  9 12:13:49 DadsLGGram kernel: [48390.110959] evdi: [I] (card2) Disconnected from Task 45118 (DesktopManagerE) of process 45106 (DisplayLinkMana)
Feb  9 12:13:49 DadsLGGram kernel: [48390.110973] evdi: [I] (card2) Removing i2c adapter bus number 16
Feb  9 12:13:49 DadsLGGram kernel: [48390.112752] evdi: [I] (card2) Closed by Task 45118 (DesktopManagerE) of process 45106 (DisplayLinkMana)
Feb  9 12:13:49 DadsLGGram kernel: [48390.119100] evdi: [W] evdi_painter_connect:883 (card1) Double connect - replacing 00000000e71cf7f0 with 00000000e71cf7f0
Feb  9 12:13:49 DadsLGGram kernel: [48390.119108] evdi: [I] (card1) Connected with Task 45118 (DesktopManagerE) of process 45106 (DisplayLinkMana)
Feb  9 12:13:49 DadsLGGram kernel: [48390.119113] evdi: [I] (card1) Connector state: connected
Feb  9 12:13:49 DadsLGGram kernel: [48390.125054] evdi: [I] (card2) Opened by Task 45118 (DesktopManagerE) of process 45106 (DisplayLinkMana)
Feb  9 12:13:49 DadsLGGram kernel: [48390.128469] evdi: [I] (card2) Added i2c adapter bus number 16
Feb  9 12:13:49 DadsLGGram kernel: [48390.128476] evdi: [I] (card2) Connected with Task 45118 (DesktopManagerE) of process 45106 (DisplayLinkMana)
Feb  9 12:13:49 DadsLGGram kernel: [48390.128480] evdi: [I] (card2) Connector state: connected
Feb  9 12:13:49 DadsLGGram kernel: [48390.225398] evdi: [I] (card2) Connector state: connected
Feb  9 12:13:49 DadsLGGram kernel: [48390.225651] evdi: [I] (card2) Edid property set
Feb  9 12:13:49 DadsLGGram kernel: [48390.225899] evdi: [I] (card2) Connector state: connected
Feb  9 12:13:49 DadsLGGram kernel: [48390.226131] evdi: [I] (card2) Edid property set
Feb  9 12:13:49 DadsLGGram kernel: [48390.716470] evdi: [I] (card1) Notifying display power state: off
Feb  9 12:13:49 DadsLGGram kernel: [48390.716477] evdi: [I] (card1) Notifying mode changed: 3840x2160@60; bpp 32; pixel format XR24 little-endian (0x34325258)
Feb  9 12:13:49 DadsLGGram kernel: [48390.716479] evdi: [I] (card1) Notifying display power state: on
Feb  9 12:13:49 DadsLGGram kernel: [48390.716509] evdi: [I] (card1) Notifying display power state: on
Feb  9 12:13:49 DadsLGGram kernel: [48390.716554] evdi: [I] (card1) Notifying mode changed: 3840x2160@60; bpp 32; pixel format XR24 little-endian (0x34325258)
Feb  9 12:13:49 DadsLGGram kernel: [48390.716556] evdi: [I] (card1) Notifying display power state: on
Feb  9 12:13:49 DadsLGGram kernel: [48390.716581] evdi: [I] (card2) Notifying mode changed: 3840x2160@60; bpp 32; pixel format XR24 little-endian (0x34325258)
Feb  9 12:13:50 DadsLGGram nxpreload.sh[6481]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
Feb  9 12:13:50 DadsLGGram nxpreload.sh[6481]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
Feb  9 12:13:50 DadsLGGram nxpreload.sh[6481]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
Feb  9 12:13:50 DadsLGGram nxpreload.sh[6481]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
Feb  9 12:13:50 DadsLGGram nxpreload.sh[6481]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
Feb  9 12:13:50 DadsLGGram nxpreload.sh[6481]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
Feb  9 12:13:50 DadsLGGram nxpreload.sh[6481]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
Feb  9 12:13:50 DadsLGGram nxpreload.sh[6481]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
Feb  9 12:13:50 DadsLGGram nxpreload.sh[6481]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
Feb  9 12:13:50 DadsLGGram kernel: [48390.716584] evdi: [I] (card2) Notifying display power state: on
Feb  9 12:13:50 DadsLGGram kernel: [48390.972434] evdi: [W] evdi_painter_connect:883 (card2) Double connect - replacing 00000000aa057b16 with 00000000aa057b16
Feb  9 12:13:50 DadsLGGram kernel: [48390.972443] evdi: [I] (card2) Connected with Task 45118 (DesktopManagerE) of process 45106 (DisplayLinkMana)
Feb  9 12:13:50 DadsLGGram kernel: [48390.972448] evdi: [I] (card2) Connector state: connected
Feb  9 12:13:50 DadsLGGram kernel: [48390.978326] evdi: [I] (card2) Notifying mode changed: 3840x2160@60; bpp 32; pixel format XR24 little-endian (0x34325258)
Feb  9 12:14:00 DadsLGGram systemd[6234]: Started Application launched by gnome-shell.
Feb  9 12:14:00 DadsLGGram dbus-daemon[6252]: [session uid=1000 pid=6252] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.456' (uid=1000 pid=54758 comm="/usr/bin/gnome-terminal.real")
Feb  9 12:14:00 DadsLGGram systemd[6234]: Starting GNOME Terminal Server...
Feb  9 12:14:01 DadsLGGram dbus-daemon[6252]: [session uid=1000 pid=6252] Successfully activated service 'org.gnome.Terminal'
Feb  9 12:14:01 DadsLGGram systemd[6234]: Started GNOME Terminal Server.
Feb  9 12:14:01 DadsLGGram systemd[6234]: Started VTE child process 54781 launched by gnome-terminal-server process 54763.

```

---

### Post by MAFoElffen on 2023-02-10
> **benjaminbreeg said:**
> [SIZE=2][FONT=trebuchet ms][COLOR=#24292F]Sometimes switching workspaces renders my two monitors blank for a few good seconds (10-15)[/COLOR], which is [COLOR=#24292F]extremely annoying. Reboot fixes it ... that is, until it starts happening again.[/COLOR]

[COLOR=#ff0000]Ubuntu 22.10, kernel 6.1.6[/COLOR][COLOR=#24292F]: [pastebin]("https://paste.ubuntu.com/p/Q2YDy5Qp7M/")
[/COLOR][/FONT][/SIZE]
On Ubuntu 22.10, the default kernel series is 5.19-x... Linux Kernel "6.1.6" is presumably meant for 6.1-rc6? 

What does it do with the default kernel? Are you using X11 or Wayland?

---

