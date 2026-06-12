---
title: "Hardy login problems"
date: 2008-06-04
forum: General Help
---

### Post by jsvidyad on 2008-06-04
Hi!!!


   I have installed the 32 bit version of hardy. But, when I try to login, I get a blank screen and in a few seconds, I am taken back to the login screen again. I tried a few times with the same result. I changed the session to Failsafe Gnome and was able to login. Why am I unable to login to normal Gnome??

   The last few lines of /var/log/syslog is given below:

Jun  4 17:36:12 mariadoss gdm[5616]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jun  4 17:36:14 mariadoss kernel: [  145.506741] [drm] Setting GART location based on new memory map
Jun  4 17:36:14 mariadoss kernel: [  145.507930] [drm] Loading R300 Microcode
Jun  4 17:36:14 mariadoss kernel: [  145.507962] [drm] writeback test succeeded in 1 usecs
Jun  4 17:36:28 mariadoss pulseaudio[6400]: pid.c: Stale PID file, overwriting.
Jun  4 17:36:30 mariadoss hcid[5064]: Default passkey agent (:1.73, /org/bluez/passkey) registered
Jun  4 17:36:30 mariadoss hcid[5064]: Default authorization agent (:1.73, /org/bluez/auth) registered
Jun  4 17:36:33 mariadoss NetworkManager: <info>  Updating allowed wireless network lists. 
Jun  4 17:36:33 mariadoss NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun  4 17:36:34 mariadoss gdm[6212]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jun  4 17:36:36 mariadoss kernel: [  167.745732] [drm] Setting GART location based on new memory map
Jun  4 17:36:36 mariadoss kernel: [  167.746959] [drm] Loading R300 Microcode
Jun  4 17:36:36 mariadoss kernel: [  167.746991] [drm] writeback test succeeded in 1 usecs
Jun  4 17:37:03 mariadoss pulseaudio[6746]: pid.c: Stale PID file, overwriting.
Jun  4 17:37:05 mariadoss hcid[5064]: Default passkey agent (:1.90, /org/bluez/passkey) registered
Jun  4 17:37:05 mariadoss hcid[5064]: Default authorization agent (:1.90, /org/bluez/auth) registered
Jun  4 17:37:08 mariadoss NetworkManager: <info>  Updating allowed wireless network lists. 
Jun  4 17:37:08 mariadoss NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun  4 17:37:09 mariadoss gdm[6545]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jun  4 17:37:12 mariadoss kernel: [  202.989122] [drm] Setting GART location based on new memory map
Jun  4 17:37:12 mariadoss kernel: [  202.990318] [drm] Loading R300 Microcode
Jun  4 17:37:12 mariadoss kernel: [  202.990350] [drm] writeback test succeeded in 1 usecs
Jun  4 17:37:32 mariadoss gdm[6891]: GLib-CRITICAL: g_key_file_get_string: assertion `key_file != NULL' failed 
Jun  4 17:37:32 mariadoss gdm[6891]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed 
Jun  4 17:37:32 mariadoss gdm[6974]: Gtk-WARNING: Ignoring the separator setting 
Jun  4 17:37:40 mariadoss pulseaudio[7040]: pid.c: Stale PID file, overwriting.
Jun  4 17:37:41 mariadoss hcid[5064]: Default passkey agent (:1.104, /org/bluez/passkey) registered
Jun  4 17:37:41 mariadoss hcid[5064]: Default authorization agent (:1.104, /org/bluez/auth) registered
Jun  4 17:37:44 mariadoss NetworkManager: <info>  Updating allowed wireless network lists. 
Jun  4 17:37:44 mariadoss NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

---

### Post by stek79 on 2008-06-30
Hi,
   the first time I boot my PC I get the same problem.

After the first failed login, though, I can enter the system.

Someone knows how to debug this?

---

