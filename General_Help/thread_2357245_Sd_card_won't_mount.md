---
title: "Sd card won't mount"
date: 2017-03-31
forum: General Help
---

### Post by bask185 on 2017-03-31
I burned a raspbian image on an sd card among with Qt but something went wrong and the rpi will not boot, and I have to start all over again. I followed this tutorial [https://wiki.qt.io/RaspberryPi_Beginners_Guide](https://wiki.qt.io/RaspberryPi_Beginners_Guide)

When I stick the SD card back in my Pc(ubuntu 16.04) I get an error message that it can't mount. It also shows up as 2 different discs with one having 66Mb. When I had this problem in windows I had to use DISKPART to make the card re-usable again. Because normal formatting would not do the trick. But now it does not even properly mount

In Ubuntu I do not know how I can make this SD card re-usable again. 

This is the systemlog [HTML]Mar 31 12:17:34 user org.gtk.vfs.Daemon[1349]: ** (process:1763): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/6 (g-dbus-error-quark, 19)
Mar 31 12:17:37 user org.gtk.vfs.Daemon[1349]: ** (gvfsd:1415): WARNING **: dbus_mount_reply: Error from org.gtk.vfs.Mountable.mount(): Failed to retrieve share list from server: Connection refused
Mar 31 12:17:37 user org.gtk.vfs.Daemon[1349]: ** (process:1908): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Mar 31 12:17:38 user gnome-session[1463]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
Mar 31 12:22:15 user dbus[942]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Mar 31 12:22:15 user systemd[1]: Starting Hostname Service...
Mar 31 12:22:15 user dbus[942]: [system] Successfully activated service 'org.freedesktop.hostname1'
Mar 31 12:22:15 user systemd[1]: Started Hostname Service.
Mar 31 12:22:17 user udisksd[1689]: Cleaning up mount point /media/user/B472-AE05 (device 8:65 is not mounted)
Mar 31 12:22:17 user udisksd[1689]: Unmounted /dev/sde1 on behalf of uid 1000
Mar 31 12:22:43 user kernel: [  391.565113] sd 8:0:0:3: [sde] 31116288 512-byte logical blocks: (15.9 GB/14.8 GiB)
Mar 31 12:22:43 user kernel: [  391.610870]  sde: sde1 sde2
Mar 31 12:22:44 user kernel: [  392.242993] EXT4-fs (sde2): bad geometry: block count 3872384 exceeds size of device (1055488 blocks)
Mar 31 12:22:44 user udisksd[1689]: Mounted /dev/sde1 at /media/user/B472-AE05 on behalf of uid 1000
Mar 31 12:22:44 user gnome-session[1463]: Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Mar 31 12:22:44 user gnome-session[1463]: (nautilus:2306): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Mar 31 12:22:44 user gnome-session[1463]: (nautilus:2306): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Mar 31 12:22:44 user gnome-session[1463]: (nautilus:2306): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
Mar 31 12:22:44 user gnome-session[1463]: (nautilus:2306): GLib-GObject-WARNING **: invalid (NULL) pointer instance
Mar 31 12:22:44 user gnome-session[1463]: (nautilus:2306): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

[/HTML]

fdisk -l gives:
[HTML]Disk /dev/sde: 14,9 GiB, 15931539456 bytes, 31116288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x432b3940

Device     Boot  Start     End Sectors Size Id Type
/dev/sde1         8192  137215  129024  63M  c W95 FAT32 (LBA)
/dev/sde2       137216 8581119 8443904   4G 83 Linux[/HTML]

Any help would be much appreciated

---

### Post by Bucky Ball on 2017-03-31
Install Gparted from the official repositories. Open it. Navigate to sde (double check that is the SD) via the drop-down menu in the top right of the GUI. 

Right click each partition and unmount. They may already be unmounted. Go to the toolbar at the top of the GUI and 'Devices> Create new partition table'. 

Did that wipe the SD?

PS: Two partitions is normal for RPi install.

---

### Post by bask185 on 2017-04-03
yeah it worked. Tnx

---

### Post by Bucky Ball on 2017-04-03
Good news. ;)

Please mark the thread as 'solved' to help others (see Thread Tools at the top right of page or instructions at link in my signature).

Enjoy.

---

