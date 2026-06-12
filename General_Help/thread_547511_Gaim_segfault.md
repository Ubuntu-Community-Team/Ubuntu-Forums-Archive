---
title: "Gaim segfault"
date: 2007-09-10
forum: General Help
---

### Post by rengolin on 2007-09-10
I can't even start gaim this morning:

$ gaim
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files
Segmentation fault (core dumped)

$ gaim --version
Gaim 2.0.0beta6

$ uname -a
Linux sbornia 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux

Ubuntu 7.04 up-to-date (universe, multiverse)

---

### Post by rengolin on 2007-09-10
Looks like it tries to connect to ICQ, fail and signal after trying to disconnect.

$ gaim -d
dbus: okkk
plugins: probing /usr/lib/gaim/autoaccept.so
plugins: probing /usr/lib/gaim/autoreply.so
plugins: probing /usr/lib/gaim/buddynote.so
plugins: probing /usr/lib/gaim/gxr.so
plugins: /usr/lib/gaim/gxr.so is not loadable: The UI requirement is not met.
plugins: probing /usr/lib/gaim/convcolors.so
plugins: probing /usr/lib/gaim/dbus-example.so
plugins: probing /usr/lib/gaim/extplacement.so
plugins: probing /usr/lib/gaim/gaimrc.so
plugins: probing /usr/lib/gaim/gestures.so
plugins: probing /usr/lib/gaim/gevolution.so
plugins: probing /usr/lib/gaim/gntgf.so
plugins: /usr/lib/gaim/gntgf.so is not loadable: The UI requirement is not met.
plugins: probing /usr/lib/gaim/gnthistory.so
plugins: /usr/lib/gaim/gnthistory.so is not loadable: The UI requirement is not met.
plugins: probing /usr/lib/gaim/gntlastlog.so
plugins: /usr/lib/gaim/gntlastlog.so is not loadable: undefined symbol: cur_term
plugins: probing /usr/lib/gaim/history.so
plugins: probing /usr/lib/gaim/iconaway.so
plugins: probing /usr/lib/gaim/idle.so
plugins: probing /usr/lib/gaim/libaim.so
plugins: probing /usr/lib/gaim/libgg.so
plugins: probing /usr/lib/gaim/libicq.so
plugins: probing /usr/lib/gaim/libirc.so
plugins: probing /usr/lib/gaim/libjabber.so
plugins: probing /usr/lib/gaim/libmsn.so
plugins: probing /usr/lib/gaim/libnovell.so
plugins: probing /usr/lib/gaim/libsametime.so
plugins: /usr/lib/gaim/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
plugins: probing /usr/lib/gaim/libqq.so
plugins: probing /usr/lib/gaim/libsimple.so
plugins: probing /usr/lib/gaim/nautilus.so
plugins: probing /usr/lib/gaim/gaim-otr.so
plugins: probing /usr/lib/gaim/libzephyr.so
plugins: /usr/lib/gaim/libzephyr.so is not loadable: libzephyr.so.3: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/libyahoo.so
plugins: probing /usr/lib/gaim/musicmessaging.so
plugins: probing /usr/lib/gaim/log_reader.so
plugins: probing /usr/lib/gaim/markerline.so
plugins: probing /usr/lib/gaim/offlinemsg.so
plugins: probing /usr/lib/gaim/newline.so
plugins: probing /usr/lib/gaim/notify.so
plugins: probing /usr/lib/gaim/psychic.so
plugins: probing /usr/lib/gaim/perl.so
plugins: probing /usr/lib/gaim/spellchk.so
plugins: probing /usr/lib/gaim/s.so
plugins: /usr/lib/gaim/s.so is not usable because the 'gaim_init_plugin' symbol could not be found.  Does the plugin call the GAIM_INIT_PLUGIN() macro?
plugins: probing /usr/lib/gaim/timestamp_format.so
plugins: probing /usr/lib/gaim/ssl-gnutls.so
plugins: probing /usr/lib/gaim/ssl-nss.so
plugins: probing /usr/lib/gaim/ssl.so
plugins: probing /usr/lib/gaim/statenotify.so
plugins: probing /usr/lib/gaim/tcl.so
plugins: probing /usr/lib/gaim/ticker.so
plugins: probing /usr/lib/gaim/timestamp.so
plugins: probing /usr/lib/gaim/xmppconsole.so
plugins: probing /usr/lib/gaim/liboscar.so
plugins: /usr/lib/gaim/liboscar.so is not usable because the 'gaim_init_plugin' symbol could not be found.  Does the plugin call the GAIM_INIT_PLUGIN() macro?
util: Reading file accounts.xml from directory /home/renato/.gaim
util: Reading file status.xml from directory /home/renato/.gaim
libnm_glib_nm_state_cb: dbus returned an error.
  (org.freedesktop.DBus.Error.ServiceUnknown) The name org.freedesktop.NetworkManager was not provided by any .service files
stun: using server
stun: using server
sound: Initializing sound output drivers.
util: Reading file blist.xml from directory /home/renato/.gaim
prefs: Reading /home/renato/.gaim/prefs.xml
prefs: Finished reading /home/renato/.gaim/prefs.xml
plugins: Loading saved plugin /usr/lib/gaim/history.so
plugins: Loading saved plugin /usr/lib/gaim/iconaway.so
plugins: Loading saved plugin /usr/lib/gaim/notify.so
plugins: Loading saved plugin /usr/lib/gaim/ssl-nss.so
plugins: Loading saved plugin /usr/lib/gaim/psychic.so
plugins: Loading saved plugin /usr/lib/gaim/ssl.so
gtkblist: added visibility manager: 1
docklet: created
Session Management: ICE initialized.
Session Management: Connecting with no previous ID
Session Management: Handling new ICE connection... done.
Session Management: Connected to manager (KDE) with client ID 10e1cbd072000118941856400000068030028
Session Management: Using gaim as command
accels: accel changed, scheduling save.
accels: accel changed, scheduling save.
dbus: Need to register an object with the dbus subsystem.
g_log: file ../../libgaim/dbus-server.c: line 118 (gaim_dbus_pointer_to_id): should not be reached
account: Connecting to account 26641517
prefs: /core/savedstatus/isidleaway changed, scheduling save.
account: Disconnecting account 0x8162840
connection: Disconnecting connection 0x860e848
Segmentation fault (core dumped)

---

