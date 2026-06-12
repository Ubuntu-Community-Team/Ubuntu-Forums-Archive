---
title: "Is there a way to find a system log for an unexpected system reboot?"
date: 2022-10-25
forum: General Help
---

### Post by alro7779 on 2022-10-25
Hey, everyone!

Yesterday I was using my Ubuntu 22.10 as usual, and then all of a sudden it rebooted. I'd like to find what caused it. I know there are various log files in **/var/log**, and I looked up already in **syslog**, but I can't find nothing there that makes me think of a culprit other than some GPU errors. Could you please give me a hand on finding the real culprit?

Thanks in advance!

---

### Post by Bashing-om on 2022-10-25
alro7779; Strange ,,,

But maybe there is a hint in the kernel's boot file.
```

journalctl -b -1   #shows messages from the precious boot
journalctl -b -0   #shows messages from the current boot

```

[INDENT]maybe - just maybe
[/INDENT]

---

### Post by mIk3_08 on 2022-10-27
> **alro7779 said:**
> Hey, everyone!

Yesterday I was using my Ubuntu 22.10 as usual, and then all of a sudden it rebooted. I'd like to find what caused it. I know there are various log files in **/var/log**, and I looked up already in **syslog**, but I can't find nothing there that makes me think of a culprit other than some GPU errors. Could you please give me a hand on finding the real culprit?

Thanks in advance!
You can also view all the system logs by running the command below. Regards and cheers.
```
cat /var/log/syslog
```

---

### Post by alro7779 on 2022-10-27
Thank you, both!

---

### Post by alro7779 on 2022-10-27
I tried this:

```
 
journalctl --since "2022-10-24" | grep "error"
oct 24 00:17:42 alejandro-ubuntu chromium_chromium.desktop[3947]: Fontconfig error: Cannot load default config file
oct 24 00:19:50 alejandro-ubuntu gnome-shell[2211]: Received error from D-Bus search provider org.gnome.Terminal.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Terminal/SearchProvider”
oct 24 00:19:51 alejandro-ubuntu gnome-shell[2211]: Received error from D-Bus search provider org.gnome.Terminal.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Terminal/SearchProvider”
oct 24 00:20:29 alejandro-ubuntu pipewire-pulse[1669]: mod.protocol-pulse: client 0x55b5028e1530: send channel:4294967295 20, error -32: Broken pipe
oct 24 00:24:15 alejandro-ubuntu udisksd[793]: Error performing housekeeping for drive /org/freedesktop/UDisks2/drives/WDC_WD10EZEX_08WN4A0_WD_WCC6Y6CS09HK: Error updating SMART data: sk_disk_smart_status: Input/output error (udisks-error-quark, 0)
oct 24 01:56:58 alejandro-ubuntu chromium_chromium.desktop[5416]: Fontconfig error: Cannot load default config file
oct 24 02:29:44 alejandro-ubuntu chromium_chromium.desktop[6721]: Fontconfig error: Cannot load default config file
oct 24 02:32:45 alejandro-ubuntu gnome-shell[2211]: Received error from D-Bus search provider org.gnome.Terminal.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Terminal/SearchProvider”
oct 24 02:32:45 alejandro-ubuntu gnome-shell[2211]: Received error from D-Bus search provider org.gnome.Terminal.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Terminal/SearchProvider”
oct 24 02:32:51 alejandro-ubuntu steam.desktop[7103]: /usr/share/themes/Yaru-dark/gtk-2.0/main.rc:775: error: unexpected identifier 'direction', expected character '}'
oct 24 02:32:51 alejandro-ubuntu steam.desktop[7103]: /usr/share/themes/Yaru-dark/gtk-2.0/hacks.rc:28: error: invalid string constant "normal_entry", expected valid string constant
oct 24 03:50:31 alejandro-ubuntu steam.desktop[7103]: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.
oct 24 03:50:31 alejandro-ubuntu thunderbird.desktop[6476]: Exiting due to channel error.
oct 24 03:50:31 alejandro-ubuntu evolution-calen[2249]: Error setting property 'ConnectionStatus' on interface org.gnome.evolution.dataserver.Source: The connection is closed (g-io-error-quark, 18)
oct 24 03:50:31 alejandro-ubuntu evolution-addre[2261]: Error setting property 'ConnectionStatus' on interface org.gnome.evolution.dataserver.Source: The connection is closed (g-io-error-quark, 18)
oct 24 03:50:33 alejandro-ubuntu /usr/libexec/gdm-x-session[1956]: (WW) xf86CloseConsole: KDSETMODE failed: Input/output error
oct 24 03:50:33 alejandro-ubuntu /usr/libexec/gdm-x-session[1956]: (WW) xf86CloseConsole: VT_GETMODE failed: Input/output error
oct 24 03:50:33 alejandro-ubuntu agent-launch[9492]: dbus-update-activation-environment: error: unable to connect to D-Bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
oct 24 11:33:32 alejandro-ubuntu systemd[1]: Process error reports when automatic reporting is enabled (file watch) was skipped because of a failed condition check (ConditionPathExists=/var/lib/apport/autoreport).
oct 24 11:33:32 alejandro-ubuntu systemd[1]: Process error reports when automatic reporting is enabled (timer based) was skipped because of a failed condition check (ConditionPathExists=/var/lib/apport/autoreport).
oct 24 11:33:42 alejandro-ubuntu pipewire-pulse[1265]: pw.conf: execvp error 'pactl': No such file or directory
oct 24 11:33:43 alejandro-ubuntu /usr/libexec/gdm-x-session[1227]:         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
oct 24 11:36:27 alejandro-ubuntu pipewire-pulse[1795]: pw.conf: execvp error 'pactl': No such file or directory
oct 24 11:36:30 alejandro-ubuntu /usr/libexec/gdm-x-session[2133]:         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
oct 24 11:36:41 alejandro-ubuntu snap-store[2443]: not handling error failed for action refresh: E: Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/kinetic/InRelease  
oct 24 11:36:43 alejandro-ubuntu snap-store[2443]: not handling error failed for action refresh: E: Failed to fetch http://mx.archive.ubuntu.com/ubuntu/dists/kinetic-updates/InRelease  
oct 24 11:45:11 alejandro-ubuntu gnome-shell[2262]: Received error from D-Bus search provider org.gnome.Terminal.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Terminal/SearchProvider”
oct 24 11:45:11 alejandro-ubuntu gnome-shell[2262]: Received error from D-Bus search provider org.gnome.Terminal.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Terminal/SearchProvider”
oct 24 11:45:11 alejandro-ubuntu gnome-shell[2262]: Received error from D-Bus search provider org.gnome.Terminal.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Terminal/SearchProvider”
oct 24 12:01:17 alejandro-ubuntu chromium_chromium.desktop[3931]: Fontconfig error: Cannot load default config file
oct 24 12:02:12 alejandro-ubuntu chromium_chromium.desktop[4967]: Fontconfig error: Cannot load default config file
oct 24 12:02:33 alejandro-ubuntu chromium_chromium.desktop[5145]: Fontconfig error: Cannot load default config file
oct 24 12:19:36 alejandro-ubuntu gnome-shell[2262]: Received error from D-Bus search provider org.gnome.Terminal.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Terminal/SearchProvider”
oct 24 12:19:37 alejandro-ubuntu gnome-shell[2262]: Received error from D-Bus search provider org.gnome.Terminal.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Terminal/SearchProvider”
oct 24 12:19:37 alejandro-ubuntu gnome-shell[2262]: Received error from D-Bus search provider org.gnome.Terminal.desktop: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Object does not exist at path “/org/gnome/Terminal/SearchProvider”
oct 24 12:19:39 alejandro-ubuntu steam.desktop[5983]: /usr/share/themes/Yaru-dark/gtk-2.0/main.rc:775: error: unexpected identifier 'direction', expected character '}'
oct 24 12:19:39 alejandro-ubuntu steam.desktop[5983]: /usr/share/themes/Yaru-dark/gtk-2.0/hacks.rc:28: error: invalid string constant "normal_entry", expected valid string constant
oct 24 12:35:28 alejandro-ubuntu gnome-shell[2262]: Unhandled promise rejection. To suppress this warning, add an error handler to your promise chain with .catch() or a try-catch block around your await expression. Stack trace of the failed promise:
oct 24 12:35:33 alejandro-ubuntu gvfsd[6560]: PTP: reading event an error 0x05 occurred
oct 24 12:35:34 alejandro-ubuntu gnome-shell[2262]: Unhandled promise rejection. To suppress this warning, add an error handler to your promise chain with .catch() or a try-catch block around your await expression. Stack trace of the failed promise:
oct 24 12:43:40 alejandro-ubuntu udisksd[782]: Error performing housekeeping for drive /org/freedesktop/UDisks2/drives/WDC_WD10EZEX_08WN4A0_WD_WCC6Y6CS09HK: Error updating SMART data: sk_disk_smart_status: Input/output error (udisks-error-quark, 0)
oct 24 13:12:28 alejandro-ubuntu gvfsd[6606]: PTP: reading event an error 0x05 occurred
oct 24 17:00:36 alejandro-ubuntu vlc[11245]: Qt: Session management error: Could not open network socket
oct 24 17:00:38 alejandro-ubuntu vlc_vlc.desktop[11245]: [00007fd688001f30] glconv_vaapi_x11 gl error: vaCreateSurfaces: attribute not supported
oct 24 17:00:38 alejandro-ubuntu vlc_vlc.desktop[11245]: [00007fd68404a920] main video output error: video output creation failed
oct 24 17:00:38 alejandro-ubuntu vlc_vlc.desktop[11245]: [00007fd6c0c1b630] main decoder error: failed to create video output
oct 24 17:00:44 alejandro-ubuntu vlc_vlc.desktop[11245]: [00007fd6c0c1b630] main decoder error: Timestamp conversion failed for 6381001: no reference clock
oct 24 17:00:44 alejandro-ubuntu vlc_vlc.desktop[11245]: [00007fd6c0c1b630] main decoder error: Could not convert timestamp 0 for FFmpeg
oct 24 17:00:44 alejandro-ubuntu vlc_vlc.desktop[11245]: [00007fd6c4031470] main input error: INPUT_CONTROL_SET_POSITION 3.7% failed
oct 24 17:00:47 alejandro-ubuntu vlc_vlc.desktop[11245]: [00007fd6c4031470] main input error: INPUT_CONTROL_SET_POSITION 6.9% failed
oct 24 17:00:47 alejandro-ubuntu vlc_vlc.desktop[11245]: [00007fd6c4031470] main input error: INPUT_CONTROL_SET_POSITION 18.7% failed
oct 24 17:00:48 alejandro-ubuntu vlc_vlc.desktop[11245]: [00007fd6c4031470] main input error: INPUT_CONTROL_SET_POSITION 28.4% failed
oct 24 17:00:49 alejandro-ubuntu vlc_vlc.desktop[11245]: [00007fd6c4031470] main input error: INPUT_CONTROL_SET_POSITION 40.8% failed
oct 24 17:00:50 alejandro-ubuntu vlc_vlc.desktop[11245]: [00007fd6c4031470] main input error: INPUT_CONTROL_SET_POSITION 51.2% failed
oct 24 17:00:52 alejandro-ubuntu gnome-shell[2262]: Unhandled promise rejection. To suppress this warning, add an error handler to your promise chain with .catch() or a try-catch block around your await expression. Stack trace of the failed promise:
oct 24 17:05:26 alejandro-ubuntu chromium_chromium.desktop[11685]: Fontconfig error: Cannot load default config file
oct 24 18:48:27 alejandro-ubuntu chromium_chromium.desktop[14030]: Fontconfig error: Cannot load default config file
oct 24 20:10:36 alejandro-ubuntu kernel: xhci_hcd 0000:02:00.0: xHC error in resume, USBSTS 0x401, Reinit
oct 24 20:11:03 alejandro-ubuntu chromium_chromium.desktop[13367]: [13367:13367:1024/201103.484282:ERROR:gpu_service_impl.cc(967)] Exiting GPU process because some drivers can't recover from errors. GPU process will restart shortly.
oct 24 20:13:27 alejandro-ubuntu udisksd[782]: Error performing housekeeping for drive /org/freedesktop/UDisks2/drives/WDC_WD10EZEX_08WN4A0_WD_WCC6Y6CS09HK: Error updating SMART data: sk_disk_smart_status: Input/output error (udisks-error-quark, 0)
oct 24 20:28:53 alejandro-ubuntu steam.desktop[16448]: [2022-10-24 20:10:44] Download failed: http error 0 (client-update.akamai.steamstatic.com/steam_client_ubuntu12)
oct 24 20:28:53 alejandro-ubuntu steam.desktop[16448]: [2022-10-24 20:10:44] Download failed: http error 0 (cdn.cloudflare.steamstatic.com/client/steam_client_ubuntu12)
oct 24 20:28:53 alejandro-ubuntu steam.desktop[16448]: [2022-10-24 20:10:44] Download failed: http error 0 (media.steampowered.com/client/steam_client_ubuntu12)
oct 24 20:28:53 alejandro-ubuntu steam.desktop[16448]: [2022-10-24 20:10:44] Error: Download failed: http error 0
oct 24 20:29:29 alejandro-ubuntu steam.desktop[5983]: [2022-10-24 20:10:44] Download failed: http error 0 (client-update.akamai.steamstatic.com/steam_client_ubuntu12)
oct 24 20:29:29 alejandro-ubuntu steam.desktop[5983]: [2022-10-24 20:10:44] Download failed: http error 0 (cdn.cloudflare.steamstatic.com/client/steam_client_ubuntu12)
oct 24 20:29:29 alejandro-ubuntu steam.desktop[5983]: [2022-10-24 20:10:44] Download failed: http error 0 (media.steampowered.com/client/steam_client_ubuntu12)
oct 24 20:29:29 alejandro-ubuntu steam.desktop[5983]: [2022-10-24 20:10:44] Error: Download failed: http error 0
oct 24 22:26:03 alejandro-ubuntu kernel: xhci_hcd 0000:02:00.0: xHC error in resume, USBSTS 0x401, Reinit
oct 24 22:28:53 alejandro-ubuntu chromium_chromium.desktop[15653]: [15653:15653:1024/222853.334043:ERROR:gpu_service_impl.cc(967)] Exiting GPU process because some drivers can't recover from errors. GPU process will restart shortly.
oct 24 23:43:08 alejandro-ubuntu steam.desktop[5983]: /usr/share/themes/Yaru/gtk-2.0/main.rc:775: error: unexpected identifier 'direction', expected character '}'
oct 24 23:43:08 alejandro-ubuntu steam.desktop[5983]: /usr/share/themes/Yaru/gtk-2.0/hacks.rc:28: error: invalid string constant "normal_entry", expected valid string constant
oct 24 23:47:03 alejandro-ubuntu chromium_chromium.desktop[19414]: Fontconfig error: Cannot load default config file

```

I don't have a clue on where could it be the culprit.

---

