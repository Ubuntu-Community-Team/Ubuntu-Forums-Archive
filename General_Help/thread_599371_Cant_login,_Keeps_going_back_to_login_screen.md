---
title: "Cant login, Keeps going back to login screen"
date: 2007-11-01
forum: General Help
---

### Post by lynxus on 2007-11-01
Hi guys,

Im trying to get desktop effects working, however im having problems with xserver-xgl

When i apt-get xserver-xgp and reload X i try to login , it does something then goes black with normal messages then goes back to the login screen.

If i remove xserver-xgl then restart X i can login again.

Ive noticed some errors in the syslog. 
Can anyone help?

Thanks
-G


Nov  1 12:53:35 broken-trumpet gdm[13292]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov  1 12:53:35 broken-trumpet kernel: [14725.652000] mtrr: no MTRR for e0000000,2000000 found
Nov  1 12:53:39 broken-trumpet kernel: [14728.944000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Nov  1 12:53:39 broken-trumpet kernel: [14728.944000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Nov  1 12:53:39 broken-trumpet kernel: [14728.944000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Nov  1 12:53:40 broken-trumpet kernel: [14730.248000] [drm] Setting GART location based on new memory map
Nov  1 12:53:40 broken-trumpet kernel: [14730.248000] [drm] Loading R200 Microcode
Nov  1 12:53:40 broken-trumpet kernel: [14730.248000] [drm] writeback test succeeded in 2 usecs
Nov  1 12:53:44 broken-trumpet gdmgreeter[13854]: GdkPixbuf-CRITICAL: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed 
Nov  1 12:53:44 broken-trumpet gdmgreeter[13854]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Nov  1 12:53:44 broken-trumpet gdmgreeter[13854]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Nov  1 12:53:44 broken-trumpet gdmgreeter[13854]: GdkPixbuf-CRITICAL: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed 
Nov  1 12:53:44 broken-trumpet gdmgreeter[13854]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Nov  1 12:53:44 broken-trumpet gdmgreeter[13854]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Nov  1 12:53:50 broken-trumpet hcid[5530]: Default passkey agent (:1.83, /org/bluez/passkey) registered
Nov  1 12:53:50 broken-trumpet hcid[5530]: Default authorization agent (:1.83, /org/bluez/auth) registered
Nov  1 12:53:54 broken-trumpet NetworkManager: <info>  Updating allowed wireless network lists. 
Nov  1 12:53:54 broken-trumpet NetworkManager: <info>  Updating VPN Connections... 
Nov  1 12:57:32 broken-trumpet kernel: [14962.652000] mtrr: no MTRR for e0000000,2000000 found
Nov  1 12:57:33 broken-trumpet gdm[13837]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Nov  1 12:57:36 broken-trumpet kernel: [14966.000000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Nov  1 12:57:36 broken-trumpet kernel: [14966.000000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Nov  1 12:57:36 broken-trumpet kernel: [14966.000000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Nov  1 12:57:37 broken-trumpet kernel: [14967.304000] [drm] Setting GART location based on new memory map
Nov  1 12:57:37 broken-trumpet kernel: [14967.304000] [drm] Loading R200 Microcode
Nov  1 12:57:37 broken-trumpet kernel: [14967.304000] [drm] writeback test succeeded in 2 usecs

---

