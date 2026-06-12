---
title: "blank screen after login/ backup permissions via livedisk"
date: 2016-10-07
forum: General Help
---

### Post by JamButty on 2016-10-07
I wiped 14 and installed the squirrel 2 months ago. For the second time in as many months, I now need to wipe and reload. Both times, after no unusual activity, no obvious trigger, the system boots and presents  a blank splash page after login. by right clicking I can get to a terminal and shut it down, but that is all. no programs are graphically available in any way. The last time this happened I spent a week trying to resolve it and finding nothing, took the data loss, wiped and reloaded with backups made just before the initial install. Now the same thing has happened, but I have a lot more stuff on HDD that I do not want to lose. So:

1. I have found a few posts with some things similar, but none describing exactly this situation. Does anybody know why this has happened and keeps happening?

2. I probably will need to wipe and reinstall. I am attempting to copy files from HDD to a thumbdrive, but run into permission problems. This link
[http://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications/270019#270019](http://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications/270019#270019)
suggests using either GKSU to invoke nautilus with privilege or sudo -H nautilus. Neither works. I cannot find GKSU for download. It is listed here
[https://apps.ubuntu.com/cat/applications/gksu/](https://apps.ubuntu.com/cat/applications/gksu/)
but using AptURL to open it gives" could not find package GKSU". Same error via Terminal after "sudo apt install gksu".
Attempting sudo -H nautilus gives
> sudo -H nautilus

(nautilus:5813): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.

** (nautilus:5813): CRITICAL **: Another desktop manager in use; desktop window won't be created
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:5813): WARNING **: Couldn't save the desktop metadata keyfile to disk: Failed to create file '/root/.config/nautilus/desktop-metadata.MCS6OY': No such file or directory

** (nautilus:5813): WARNING **: Couldn't save the desktop metadata keyfile to disk: Failed to create file '/root/.config/nautilus/desktop-metadata.D8U6OY': No such file or directory


thanks!

---

### Post by xuser2 on 2016-10-09
Verify that your disk isn't damaged or full .

If its all good , launch a gui program by terminal and post the output .

---

### Post by JamButty on 2016-10-10
xuser2
no damage or space problems. I've been through the basic check on the safe mode boot. I can invoke nautilus via the terminal, and other filetype invoked programs from there (e.g. a txt invoking gui text editor). I have not worked out all the commands, but since I can use the terminal as the normal, authorized user, I should be able to copy files over to an external HDD and fix the permissions for later restore. I would like to find out why this is happening though, since it has happened twice in two months. I am on the dark side now - will reboot now to the squirrel and see if I can capture the output you requested onto the windows partition. Not sure how to invoke a browser via terminal to get back here.

Here is the terminal output on invoking nautilus. I note that it is not fully functional e.g. no task bar, locked in a odd full screen configuration that I can only exit via function keys.
> (nautilus:2101): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:2101): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:2101): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:2101): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:2101): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed



---

### Post by JamButty on 2016-10-14
did backup/wipe/reinstall. Not marking solved as I have not found any explanation for why this happens repeatedly.

---

