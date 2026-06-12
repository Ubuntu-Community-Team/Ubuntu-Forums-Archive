---
title: "Gnome Appearance Properties freezing"
date: 2007-08-06
forum: General Help
---

### Post by GeneralHooHa on 2007-08-06
When I run gnome-appearance-properties, either through the terminal or from System -> Preferences -> Appearance, it stops responding after a few seconds. Here is the terminal output: 
```
nick@Private-Laptop:~$ gnome-appearance-properties

(gnome-appearance-properties:7554): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gnome-appearance-properties:7554): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gnome-appearance-properties:7554): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gnome-appearance-properties:7554): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gnome-appearance-properties:7554): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gnome-appearance-properties:7554): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gnome-appearance-properties:7554): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gnome-appearance-properties:7554): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gnome-appearance-properties:7554): appearance-properties-WARNING **: Unknown Tag: comment


(gnome-appearance-properties:7554): appearance-properties-WARNING **: Unknown Tag: comment

/usr/share/themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(gnome-appearance-properties:7555): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed

(gnome-appearance-properties:7555): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed
nick@Private-Laptop:~$
```
Does anybody have a clue as to what is happening? Is there a way that I can re-install it?

---

### Post by iamhimay on 2007-09-23
Hi, 
Did you ever resolve this issue? I'm racking my brain. I noticed my friend who upgraded from feisty to gutsy does not have this problem. I started from tribe2 and have been updating regularly. Any info would be appreciated. 
Thanks,
 (iamhimay)

---

### Post by figjam on 2007-09-25
My issue is the same as well. However I am running Gutsy.

whenever I start the app I get the following output:

:~$  gnome-appearance-properties
/bin/sh: /usr/bin/esd: not found
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'

(gnome-appearance-properties:11455): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed

(gnome-appearance-properties:11455): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed

:~$ sudo apt-get install esd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package esd

:~$ ls -l /etc/qt3/qt_plugins_3.3rc
-rw-r----- 1 root root 642 2007-09-01 11:28 /etc/qt3/qt_plugins_3.3rc

---

### Post by figjam on 2007-09-25
I ran this manually:

gnome-appearance-properties --show-page=effects

The windows appeared, with the right tab selected. However I could not click on anything but down arrow seemed to have selected something, which brought up a blank window, to which I pressed Enter. It did change the effects.

However, subsequent tries with the same command results in:


"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

Below is the output from the first session:

~:$ gnome-appearance-properties --show-page=effects
/bin/sh: /usr/bin/esd: not found

(gnome-appearance-properties:11602): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed

(gnome-appearance-properties:11602): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed
No nvidia hardware available
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:29c2 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


gary@darkstar:~$ sudo gnome-appearance-properties --show-page=effects
/bin/sh: /usr/bin/esd: not found

(gnome-appearance-properties:11719): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed

(gnome-appearance-properties:11719): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed

---

### Post by figjam on 2007-09-25
Update:

It works if you run it as root, not via sudo though.

i did this:

:$ sudo su
:$ gnome-appearance-properties




(gnome-appearance-properties:9801): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
No nvidia hardware available
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:29c2 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
 

=====

I did however get the following popup as soon as it started

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

---

### Post by Offoffoff on 2007-09-28
Same is here in my Gutsy Gibbon! I have installed server-xgl, then I removed it in spite of its malfunction, then I am getting errors You all people described here.

---

### Post by wersdaluv on 2007-09-29
It happens to me too. 

I filed a bug report.

---

### Post by figjam on 2007-09-30
I had gtk-qt-engine installed. I removed it and it worked!

Here is a thread that resolved it for me:
[https://bugs.launchpad.net/bugs/138726](https://bugs.launchpad.net/bugs/138726)

sudo apt-get remove gtk-qt-engine

---

### Post by Derspankster on 2007-10-27
> **figjam said:**
> I had gtk-qt-engine installed. I removed it and it worked!

Here is a thread that resolved it for me:
[https://bugs.launchpad.net/bugs/138726](https://bugs.launchpad.net/bugs/138726)

sudo apt-get remove gtk-qt-engine

Worked like a charm for me. Thanks!!

---

### Post by gregili on 2007-10-29
worked for me too ..

---

### Post by steve_waters on 2008-01-15
Can the author change this thread to (solved), but great who ever work this out.

---

### Post by charonn0 on 2008-01-30
And for me as well.\\:D/

Many, many thanks! I was approaching near homicidal rage!](*,)

---

### Post by madhatt3r on 2008-03-16
Hi fellas,

and what if the gtk-qt-engine is not installed ? :p

I'm running on a fresh-installed Debian Sid, with Gnome obviously (2.20), and I get the same problem : the appearance window freezes a few seconds after opening...

Any other solution ?

---

