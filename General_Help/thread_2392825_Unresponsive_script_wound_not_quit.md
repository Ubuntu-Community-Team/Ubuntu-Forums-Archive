---
title: "Unresponsive script wound not quit"
date: 2018-05-25
forum: General Help
---

### Post by Gnusboy on 2018-05-25
Hello

I just had a strange thing happen. My system was locking up and I could not close windows or do anything for more than 5 minutes. It finally show there a non responsive script, but it flashed by too fast to read
and I could not see where it was located. It did this about three times during the system lockup. I had 3 open pages in Libre Office and I was able to close those. But Firefox was keeping the browser locked and I could not close
any windows without being locked. I was finally able to close 4 of the 5 open windows. I was trying to see the location of where the unresposive script.
After the long problem, I went wenbt to the sys log to see if the problem was showing. 

On the log shown below, I see a multitude of time outs that are not anything I have seen before. 

So, what I show here looks like the time out started at about 13:36 p.m. But these early ones did not impact the function of my system until 17:39 p.m.
Between 17:39 p.m. and 18:16 p.m.

I am deleting all the rest of the entries for the sake of brevity. I have them if needed.



```


May 25 13:15:11 ranha-system org.debian.apt[822]: 13:15:11 AptDaemon.Worker [INFO]: Finished transaction /org/debian/apt/transaction/7ae42c132a534e42ac5adf0b288a61f5
May 25 13:17:02 ranha-system CRON[8188]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 25 13:20:39 ranha-system gnome-session[1665]: (gnome-software:1839): Gs-WARNING **: failed to call gs_plugin_add_search on appstream: Operation was cancelled
May 25 13:20:40 ranha-system gnome-session[1665]: message repeated 2 times: [ (gnome-software:1839): Gs-WARNING **: failed to call gs_plugin_add_search on appstream: Operation was cancelled]
May 25 13:20:40 ranha-system gnome-session[1665]: (gnome-software:1839): Gs-WARNING **: failed to call gs_plugin_add_search on snap: Operation was cancelled
May 25 13:20:41 ranha-system gnome-session[1665]: (gnome-software:1839): Gs-WARNING **: failed to call gs_plugin_add_search on snap: Operation was cancelled
May 25 13:21:46 ranha-system AptDaemon: INFO: UpdateCache() was called
May 25 13:21:46 ranha-system org.debian.apt[822]: 13:21:46 AptDaemon [INFO]: UpdateCache() was called
May 25 13:21:46 ranha-system AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/0031735b11aa4248970a91e0b7b05fc2
May 25 13:21:46 ranha-system AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/0031735b11aa4248970a91e0b7b05fc2
May 25 13:21:46 ranha-system org.debian.apt[822]: 13:21:46 AptDaemon.Trans [INFO]: Queuing transaction /org/debian/apt/transaction/0031735b11aa4248970a91e0b7b05fc2
May 25 13:21:46 ranha-system org.debian.apt[822]: 13:21:46 AptDaemon.Worker [INFO]: Simulating trans: /org/debian/apt/transaction/0031735b11aa4248970a91e0b7b05fc2
May 25 13:21:46 ranha-system AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/0031735b11aa4248970a91e0b7b05fc2
May 25 13:21:46 ranha-system org.debian.apt[822]: 13:21:46 AptDaemon.Worker [INFO]: Processing transaction /org/debian/apt/transaction/0031735b11aa4248970a91e0b7b05fc2
May 25 13:21:47 ranha-system AptDaemon.Worker: INFO: Updating cache
May 25 13:21:47 ranha-system org.debian.apt[822]: 13:21:47 AptDaemon.Worker [INFO]: Updating cache
May 25 13:21:56 ranha-system AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/0031735b11aa4248970a91e0b7b05fc2
May 25 13:21:56 ranha-system org.debian.apt[822]: 13:21:56 AptDaemon.Worker [INFO]: Finished transaction /org/debian/apt/transaction/0031735b11aa4248970a91e0b7b05fc2
May 25 13:21:56 ranha-system gnome-session[1665]: (gnome-software:1839): Gs-WARNING **: failed to refresh: apt transaction returned result exit-failed
May 25 13:22:14 ranha-system gnome-session[1665]: /usr/bin/update-manager:28: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
May 25 13:22:15 ranha-system gnome-session[1665]:   from gi.repository import Gtk
May 25 13:22:15 ranha-system gnome-session[1665]: /usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Dbusmenu was imported without specifying a version first. Use gi.require_version('Dbusmenu', '0.4') before import to ensure that the right version gets loaded.

```

```

May 25 17:28:57 ranha-system systemd[1]: Time has been changed
May 25 17:28:57 ranha-system systemd[1443]: Time has been changed
May 25 17:31:16 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 17:31:59 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 17:32:09 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 17:32:19 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).

```

```

May 25 17:32:20 ranha-system systemd[1443]: Time has been changed
May 25 17:32:20 ranha-system systemd-timesyncd[500]: Synchronized to time server 91.189.89.198:123 (ntp.ubuntu.com).
May 25 17:32:20 ranha-system systemd[1]: Time has been changed
May 25 17:34:39 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 17:35:21 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 17:35:31 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 17:35:42 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 17:35:52 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
May 25 17:37:06 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 17:37:07 ranha-system systemd-timesyncd[500]: Synchronized to time server 91.189.89.199:123 (ntp.ubuntu.com).

May 25 17:37:07 ranha-system systemd[1]: Time has been changed
May 25 17:37:07 ranha-system systemd[1443]: Time has been changed
 
```

```

May 25 17:39:26 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 17:39:36 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 17:39:46 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
May 25 17:40:29 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 17:40:39 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
May 25 17:40:49 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 17:41:00 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 17:42:14 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 17:42:24 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 17:42:35 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
May 25 17:42:45 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 17:45:03 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
May 25 17:45:14 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 17:45:24 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 17:45:34 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 17:50:01 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 17:50:11 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
May 25 17:50:21 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 17:50:31 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 17:59:14 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 17:59:24 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
May 25 17:59:27 ranha-system systemd-timesyncd[500]: Synchronized to time server 91.189.89.199:123 (ntp.ubuntu.com).

```


```

May 25 17:59:27 ranha-system systemd[1]: Time has been changed
May 25 17:59:27 ranha-system systemd[1443]: Time has been changed
May 25 18:01:47 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 18:01:57 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 18:02:03 ranha-system dbus[822]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
May 25 18:02:07 ranha-system org.gtk.vfs.Daemon[1532]: ** (process:1917): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/1 (g-dbus-error-quark, 19)
May 25 18:02:08 ranha-system org.gtk.vfs.Daemon[1532]: message repeated 3 times: [ ** (process:1917): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/1 (g-dbus-error-quark, 19)]
May 25 18:02:08 ranha-system org.gtk.vfs.Daemon[1532]: ** (process:1917): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/1 (g-dbus-error-quark, 19)

```

```

May 25 18:02:08 ranha-system systemd[1]: Starting Hostname Service...
May 25 18:02:08 ranha-system dbus[822]: [system] Successfully activated service 'org.freedesktop.hostname1'
May 25 18:02:08 ranha-system systemd[1]: Started Hostname Service.
May 25 18:02:39 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 18:02:50 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 18:03:00 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
May 25 18:03:00 ranha-system systemd[1]: Time has been changed
May 25 18:03:00 ranha-system systemd[1443]: Time has been changed
May 25 18:03:00 ranha-system systemd-timesyncd[500]: Synchronized to time server 91.189.91.157:123 (ntp.ubuntu.com).
May 25 18:08:35 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 18:09:17 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 18:09:27 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
May 25 18:09:38 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 18:09:48 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 18:11:02 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 18:11:13 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
May 25 18:11:23 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 18:11:33 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).

```
```

May 25 18:13:19 ranha-system gnome-session[1665]: gnome-session-binary[1665]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
May 25 18:13:19 ranha-system gnome-session[1665]: gnome-session-binary[1665]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
May 25 18:13:19 ranha-system gnome-session-binary[1665]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
May 25 18:13:19 ranha-system gnome-session-binary[1665]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
May 25 18:13:20 ranha-system gnome-session[1665]: gnome-session-binary[1665]: WARNING: Client '/org/gnome/SessionManager/Client4' failed to reply before timeout
May 25 18:13:20 ranha-system gnome-session-binary[1665]: WARNING: Client '/org/gnome/SessionManager/Client4' failed to reply before timeout
May 25 18:13:20 ranha-system gnome-session[1665]: gnome-session-binary[1665]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
May 25 18:13:20 ranha-system gnome-session-binary[1665]: GLib-GObject-CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

```
```

May 25 18:13:41 ranha-system gnome-session-binary[1665]: Entering running state
May 25 18:13:52 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
May 25 18:14:02 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
May 25 18:14:12 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
May 25 18:14:22 ranha-system systemd-timesyncd[500]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
May 25 18:16:41 ranha-system rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="819" x-info="http://www.rsyslog.com"] start
May 25 18:16:41 ranha-system rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ]
May 25 18:16:41 ranha-system rsyslogd: rsyslogd's groupid changed to 108
May 25 18:16:41 ranha-system rsyslogd: rsyslogd's userid changed to 104

```

---

### Post by Gnusboy on 2018-05-26
Gads. I thought I had trimmed this to something manageable. Sorry for hte goof.

---

