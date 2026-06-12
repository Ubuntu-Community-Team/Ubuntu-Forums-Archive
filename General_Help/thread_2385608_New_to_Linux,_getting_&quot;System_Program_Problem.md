---
title: "New to Linux, getting &quot;System Program Problem Detected&quot;"
date: 2018-02-22
forum: General Help
---

### Post by saj1420 on 2018-02-22
I am new to linux, but a customer of mine wanted Ubuntu on some rigs I am building for him.  I got it installed with no issues, but I keep getting an error that says "System Program Problem Detected" I found the system log, and I have pasted below the errors that I see, could this be what is causing the program error? Can anyone tell me what these mean or how to fix them?

Thank you,

I tried attaching the entire log but I cant figure it out

```
Feb 22 09:35:34 ZJ dbus[716]: [system] Activating via systemd: service name='org.freedesktop.locale1' unit='dbus-org.freedesktop.locale1.service'
Feb 22 09:35:34 ZJ systemd[1]: Starting Locale Service...
Feb 22 09:35:34 ZJ dbus[716]: [system] Successfully activated service 'org.freedesktop.locale1'
Feb 22 09:35:34 ZJ systemd[1]: Started Locale Service.
Feb 22 09:35:34 ZJ gnome-session-binary[1354]: Entering running state
Feb 22 09:35:34 ZJ gnome-session[1354]: (process:1682): indicator-application-service-WARNING **: Unable to get watcher name 'org.kde.StatusNotifierWatcher'
Feb 22 09:35:34 ZJ gnome-session[1354]: (process:1682): indicator-application-service-WARNING **: Name Lost
Feb 22 09:35:34 ZJ dbus[716]: [system] Activating service name='org.freedesktop.fwupd' (using servicehelper)
Feb 22 09:35:34 ZJ gnome-session[1354]: (nautilus:1683): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Feb 22 09:35:34 ZJ gnome-session[1354]: (nautilus:1683): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Feb 22 09:35:34 ZJ gnome-session[1354]: (nautilus:1683): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Feb 22 09:35:34 ZJ gnome-session[1354]: (nautilus:1683): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Feb 22 09:35:34 ZJ gnome-session[1354]: (nautilus:1683): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed
Feb 22 09:35:35 ZJ udisksd[1599]: Mounted /dev/sdb1 at /media/zj/B477-C995 on behalf of uid 1000
Feb 22 09:35:35 ZJ dbus[716]: [system] Successfully activated service 'org.freedesktop.fwupd'
Feb 22 09:35:36 ZJ com.canonical.Unity.Scope.Applications[1179]: Error loading package indexes: Couldn't stat '/var/cache/software-center/xapian'
Feb 22 09:35:36 ZJ com.canonical.Unity.Scope.Applications[1179]: (unity-scope-loader:1749): unity-applications-daemon-CRITICAL **: daemon.vala:144: Failed to load Software Center index. 'Apps Available for Download' will not be listed
Feb 22 09:35:54 ZJ gnome-session[1354]: ** (zeitgeist-datahub:1823): WARNING **: zeitgeist-datahub.vala:229: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Feb 22 09:36:08 ZJ systemd[1]: Starting Stop ureadahead data collection...
Feb 22 09:36:08 ZJ systemd[1]: Stopped Read required files in advance.
Feb 22 09:36:08 ZJ systemd[1]: Started Stop ureadahead data collection.
Feb 22 09:36:39 ZJ gnome-session[1354]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
```

---

### Post by deadflowr on 2018-02-22
Crash reports are stored in /var/crash.
Look in there for whatever the issues are.

Any files in there will be opened by the systems crash reporting program if you click on them.
They're long, and I'm not sure how to post them outside of screenshots, but you can post a screen shot of just the fiorst part.
Since the relevant info like what program has crashed will show in the beginning of the output.

Or just post what program it tells you has crashed.

---

### Post by VMC on 2018-02-22
Deleting the crash files can sometime fix the issues:
[https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/](https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/)
[https://ubuntuforums.org/showthread.php?t=2317249](https://ubuntuforums.org/showthread.php?t=2317249)

After deleting the crash files, on reboot what happens?

---

