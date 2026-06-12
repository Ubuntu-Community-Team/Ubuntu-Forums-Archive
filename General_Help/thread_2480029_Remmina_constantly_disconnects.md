---
title: "Remmina constantly disconnects"
date: 2022-10-16
forum: General Help
---

### Post by inator-maker on 2022-10-16
I am running Ubuntu 22.04 LTS.  I have a Windows 10 VM running from my unRAID server.  This VM manages my Blue Iris instance.  When I connect and stare at the desktop all is well.  When trying to use Blue Iris or anything other than just look at the desktop Remmina will disconnect within about 5 seconds. Remmina is v1.4.27.

Not even sure where to start trouble shooting this.

---

### Post by #&amp;thj^% on 2022-10-16
Start it from the terminal, and on next crash or close, copy that back here so we can try to see whats going on.
```
remmina
```]

---

### Post by inator-maker on 2022-10-16
```
remmina-Message: 16:43:30.903: Remmina does not log all output statements. Turn on more verbose output by using "G_MESSAGES_DEBUG=all" as an environment variable.More info available on the Remmina wiki at:
https://gitlab.com/Remmina/Remmina/-/wikis/Usage/Remmina-debugging
Load modules from /usr/lib/x86_64-linux-gnu/remmina/plugins
Remmina plugin glibsecret (type=Secret) has been registered, but is not yet initialized/activated. The initialization order is 2000.
The glibsecret secret plugin has been initialized and it will be your default secret plugin


(org.remmina.Remmina:12574): Gtk-WARNING **: 16:43:30.975: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
[16:43:38:045] [12574:12603] [ERROR][com.freerdp.common.settings] - [freerdp_settings_get_bool] Invalid key index 131
[16:43:38:045] [12574:12603] [ERROR][com.freerdp.common.settings] - [freerdp_settings_get_bool] Invalid key index 0
[16:43:39:362] [12574:12603] [WARN][com.freerdp.crypto] - Certificate verification failure 'self-signed certificate (18)' at stack position 0
[16:43:39:362] [12574:12603] [WARN][com.freerdp.crypto] - CN = BlueIris
[16:43:40:664] [12574:12603] [INFO][com.freerdp.gdi] - Local framebuffer format  PIXEL_FORMAT_BGRX32
[16:43:40:664] [12574:12603] [INFO][com.freerdp.gdi] - Remote framebuffer format PIXEL_FORMAT_RGB16
[16:43:40:664] [12574:12603] [INFO][com.freerdp.channels.rdpsnd.client] - [static] Loaded fake backend for rdpsnd
[16:43:40:664] [12574:12603] [INFO][com.freerdp.channels.drdynvc.client] - Loading Dynamic Virtual Channel disp
[16:45:07:673] [12574:12603] [ERROR][com.freerdp.core.transport] - BIO_read returned a system error 110: Connection timed out
[16:45:07:673] [12574:12603] [ERROR][com.freerdp.core] - transport_read_layer:freerdp_set_last_error_ex ERRCONNECT_CONNECT_TRANSPORT_FAILED [0x0002000D]
[16:45:13:236] [12574:12603] [INFO][com.freerdp.channels.rdpsnd.client] - [static] Loaded fake backend for rdpsnd
[16:45:13:236] [12574:12603] [INFO][com.freerdp.channels.drdynvc.client] - Loading Dynamic Virtual Channel disp
[16:45:19:075] [12574:12603] [ERROR][com.freerdp.gdi.region] - [gdi_RectToCRgn] rectangle invalid [top/left=320x909-bottom/right383x831]
[16:45:19:104] [12574:12603] [ERROR][com.freerdp.gdi.region] - [gdi_RectToCRgn] rectangle invalid [top/left=320x909-bottom/right383x831]
[16:45:19:143] [12574:12603] [ERROR][com.freerdp.gdi.region] - [gdi_RectToCRgn] rectangle invalid [top/left=320x909-bottom/right383x831]



```

---

### Post by #&amp;thj^% on 2022-10-16
here is what I see with no solution offered yet. (I need to think)
```
[ERROR][com.freerdp.core.transport] - BIO_read returned a system error 110: Connection timed out
[16:45:07:673] [12574:12603] [ERROR][com.freerdp.core] - transport_read_layer:freerdp_set_last_error_ex ERRCONNECT_CONNECT_TRANSPORT_FAILED [0x0002000D]
[16:45:13:236] [12574:12603] [INFO][com.freerdp.channels.rdpsnd.client] - [static] Loaded fake backend for rdpsnd
```
Aaaha This could be the villain here:
```
[16:43:38:045] [12574:12603] [ERROR][com.freerdp.common.settings] - [freerdp_settings_get_bool] Invalid key index 131
[16:43:38:045] [12574:12603] [ERROR][com.freerdp.common.settings] - [freerdp_settings_get_bool] Invalid key index 0
[16:43:39:362] [12574:12603] [WARN][com.freerdp.crypto] - Certificate verification failure 'self-signed certificate (18)' at stack position 0
[16:43:39:362] [12574:12603] [WARN][com.freerdp.crypto] - CN = BlueIris
```
Mine still running strong with no such error's to see
```
remmina-Message: 14:35:33.085: Remmina does not log all output statements. Turn on more verbose output by using "G_MESSAGES_DEBUG=all" as an environment variable.
More info available on the Remmina wiki at:
https://gitlab.com/Remmina/Remmina/-/wikis/Usage/Remmina-debugging
Load modules from /usr/lib/remmina/plugins
Failed to load plugin: /usr/lib/remmina/plugins/remmina-plugin-rdp.so.
Error: libfreerdp2.so.2: cannot open shared object file: No such file or directory
Remmina plugin kwallet (type=Secret) has been registered, but is not yet initialized/activated. The initialization order is 1000.
Failed to load plugin: /usr/lib/remmina/plugins/remmina-plugin-vnc.so.
Error: libvncclient.so.1: cannot open shared object file: No such file or directory
Remmina plugin glibsecret (type=Secret) has been registered, but is not yet initialized/activated. The initialization order is 2000.
** Message: 14:35:33.181: [X2GO] X2Go plugin loaded.
The glibsecret secret plugin has been initialized and it will be your default secret plugin

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:35:33.205: Theme parsing error: gtk.css:4091:13: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:35:33.214: Theme parsing error: gtk.css:7855:13: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:35:33.214: Theme parsing error: gtk.css:8039:19: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:35:33.215: Theme parsing error: gtk.css:8317:21: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:35:33.215: Theme parsing error: gtk.css:8318:24: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:35:33.287: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:35:33.297: Theme parsing error: gtk.css:4091:13: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:35:33.303: Theme parsing error: gtk.css:7855:13: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:35:33.303: Theme parsing error: gtk.css:8039:19: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:35:33.304: Theme parsing error: gtk.css:8317:21: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:35:33.304: Theme parsing error: gtk.css:8318:24: negative values are not allowed.

(chromium:986075): Gtk-WARNING **: 14:35:56.413: Theme parsing error: gtk.css:4091:13: negative values are not allowed.

(chromium:986075): Gtk-WARNING **: 14:35:56.420: Theme parsing error: gtk.css:7855:13: negative values are not allowed.

(chromium:986075): Gtk-WARNING **: 14:35:56.420: Theme parsing error: gtk.css:8039:19: negative values are not allowed.

(chromium:986075): Gtk-WARNING **: 14:35:56.421: Theme parsing error: gtk.css:8317:21: negative values are not allowed.

(chromium:986075): Gtk-WARNING **: 14:35:56.421: Theme parsing error: gtk.css:8318:24: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:39:55.027: Theme parsing error: gtk.css:4091:13: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:39:55.034: Theme parsing error: gtk.css:7855:13: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:39:55.034: Theme parsing error: gtk.css:8039:19: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:39:55.035: Theme parsing error: gtk.css:8317:21: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:39:55.035: Theme parsing error: gtk.css:8318:24: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:40:22.117: Theme parsing error: gtk.css:4091:13: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:40:22.123: Theme parsing error: gtk.css:7855:13: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:40:22.124: Theme parsing error: gtk.css:8039:19: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:40:22.124: Theme parsing error: gtk.css:8317:21: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:40:22.124: Theme parsing error: gtk.css:8318:24: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:41:05.771: Theme parsing error: gtk.css:4091:13: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:41:05.781: Theme parsing error: gtk.css:7855:13: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:41:05.782: Theme parsing error: gtk.css:8039:19: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:41:05.782: Theme parsing error: gtk.css:8317:21: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:41:05.782: Theme parsing error: gtk.css:8318:24: negative values are not allowed.

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:41:05.897: Negative content width -5 (allocation 1, extents 3x3) while allocating gadget (node button, owner GtkToggleButton)

(org.remmina.Remmina:985126): Gtk-WARNING **: 14:41:05.897: Negative content height -5 (allocation 1, extents 3x3) while allocating gadget (node button, owner GtkToggleButton)

(org.remmina.Remmina:985126): GLib-GIO-CRITICAL **: 14:41:06.014: g_file_new_for_path: assertion 'path != NULL' failed

(org.remmina.Remmina:985126): GLib-GIO-CRITICAL **: 14:41:06.014: g_file_get_basename: assertion 'G_IS_FILE (file)' failed

(org.remmina.Remmina:985126): GLib-GIO-CRITICAL **: 14:41:17.016: g_file_new_for_path: assertion 'path != NULL' failed

(org.remmina.Remmina:985126): GLib-GIO-CRITICAL **: 14:41:17.021: g_file_get_basename: assertion 'G_IS_FILE (file)' failed

```

---

### Post by inator-maker on 2022-10-16
I have a feeling it has something to do with an issue related to graphics, but I'm not sure.  I assume the logs you posted are into a Windows VM?  Is is on your local machine or server?  Either way can you post your connection settings if they are other than default?

---

### Post by #&amp;thj^% on 2022-10-16
all default see screenshot.
this needs some attention though on your end:
```
[16:43:38:045] [12574:12603] [ERROR][com.freerdp.common.settings] - [freerdp_settings_get_bool] **Invalid key index 131**
[16:43:38:045] [12574:12603] [ERROR][com.freerdp.common.settings] - [freerdp_settings_get_bool] **Invalid key index 0**
[16:43:39:362] [12574:12603] [WARN][com.freerdp.crypto] - **Certificate verification failure 'self-signed certificate (18)' at stack position 0**
[16:43:39:362] [12574:12603] [WARN][com.freerdp.crypto] -** CN = BlueIris**
```

---

### Post by inator-maker on 2022-10-16
thanks for the screen shot.  I have no idea where to even start troubleshooting this.

---

### Post by HermanAB on 2022-10-17
My guess is that it crashes immediately and that you are actually staring at a dead screen.

The usual fix would be to see if there are upgrades available and if not, try to downgrade the utility and see if a previous version works.  The previous version may have different less severe bugs that you won’t notice.

---

### Post by #&amp;thj^% on 2022-10-17
> **inator-maker said:**
> I have a feeling it has something to do with an issue related to graphics, but I'm not sure.  I assume the logs you posted are into a Windows VM?  Is is on your local machine or server?  Either way can you post your connection settings if they are other than default?
If your trying to connect to a Windows OS give this a try,  edit the connection properties, I looked on the "advanced" tab and changed the security from "negotiate" to "TLS", and voila, everything works.

---

### Post by inator-maker on 2022-10-17
> **1fallen said:**
> If your trying to connect to a Windows OS give this a try,  edit the connection properties, I looked on the "advanced" tab and changed the security from "negotiate" to "TLS", and voila, everything works.


I tried this and Remmina fails to connect.

---

### Post by #&amp;thj^% on 2022-10-17
> **inator-maker said:**
> I tried this and Remmina fails to connect.

These folks might be of better help: [https://github.com/FreeRDP/FreeRDP/issues/6604](https://github.com/FreeRDP/FreeRDP/issues/6604)

---

