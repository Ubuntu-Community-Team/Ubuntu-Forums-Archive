---
title: "X not starting in Ubuntu 12.04"
date: 2014-01-22
forum: General Help
---

### Post by sir_robert007 on 2014-01-22
So after what I am assuming was an update X refuses to start up on my computer. Every time I start my computer it goes to command prompt only. I then tried to start X via command prompt using sudo service lightdm start to no avail. What can I do to fix this problem? Would it require me to edit something in xorg.conf or another configuration file? 

System Specs:

Ubuntu 12.04 64 bit
Processor AMD Phenom II 810 2.6 ghz
4gb ram
1TB hard Drive

---

### Post by jeanjd63 on 2014-01-22
Hello

What is the return of command :
**startx**

---

### Post by sir_robert007 on 2014-01-22
> **jeanjd63 said:**
> Hello

What is the return of command :
**startx**


Tried **startx** but it still didn't work. What ended up happening after i executed the command was a bunch of text flew by then the system became unresponsive. Tried Ctrl - C to stop the process but couldn't. Also i couldn't switch to a different terminal using Ctrl - Alt - F1, F2, etc. Is there a way i can capture the output and save it to a text file then upload it in a post for everyone to read?

---

### Post by jp734 on 2014-01-22
you can look at the /var/log/Xorg.0.log to see why it failed.

---

### Post by Bashing-om on 2014-01-22
sir_robert007; Hi !

This situation often occurs when proprietary graphics drivers are installed; Does this apply in your case ?

Can you boot via grub's recovery console to a GUI desktop ?

The cause can be investigated, this though is a "reasonable" place to start.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Kr0nZ on 2014-01-22
though it would help if you actually gave the output of ''startx', instead of "[COLOR=#000000]a bunch of text flew[/COLOR]"

But I also recently tried updating my X11 to the dev version which caused X not to start properly, to fix it I just did 'sudo apt-get install xorg' then xstart worked, the destop was still a little funky tho until I restarted.

---

### Post by sir_robert007 on 2014-01-23
> **Bashing-om said:**
> sir_robert007; Hi !

This situation often occurs when proprietary graphics drivers are installed; Does this apply in your case ?

Can you boot via grub's recovery console to a GUI desktop ?

The cause can be investigated, this though is a "reasonable" place to start.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

Yes I have proprietary drivers installed. They worked until an update caused them to fail and it reverted back to the open source drivers. It worked fine like this for a long time though I was unable to use 3d apps like team fortress 2 until recently when the X server failed to start altogether. Tried booting into fail safe X. Still no luck.

---

### Post by Bashing-om on 2014-01-23
sir_robert007; UMPHH,

Not a good sign.

Let's check and make sure the base system is stable and then see what the graphics situation is.
Boot to grub's boot menu, Latest "normal" kernel highlighted -> "e" key for edit mode;
Arrow down and across to the terms "quiet splash" enter this term "text" and delete "quiet splash";
key combo ctl+x to continue the boot process to a text login (TTY1) terminal.
Log in , enter your password.
What is the result of terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
Of interest here is - for example - my output:
> 
lshw:
 description: VGA compatible controller
       product: RV515 [Radeon X1300/X1550]
<snip>
##and##
configuration: driver=radeon latency=0
<snip>

lspci:
sysop@1310mini:~$ lspci -nnk | grep -iA3 vga
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550] [1002:7146]
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:2342]
        Kernel driver in use: radeon
06:00.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary) [1002:7166]
sysop@1310mini:~$ 
##which shows the graphic cards in use ##

Now we can see about cleaning things up and getting a driver installed onto the system.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by sir_robert007 on 2014-01-23
> **Bashing-om said:**
> sir_robert007; UMPHH,

Not a good sign.

Let's check and make sure the base system is stable and then see what the graphics situation is.
Boot to grub's boot menu, Latest "normal" kernel highlighted -> "e" key for edit mode;
Arrow down and across to the terms "quiet splash" enter this term "text" and delete "quiet splash";
key combo ctl+x to continue the boot process to a text login (TTY1) terminal.
Log in , enter your password.
What is the result of terminal codes:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
Of interest here is - for example - my output:

Now we can see about cleaning things up and getting a driver installed onto the system.[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]
[/INDENT]



Ok so i followed your instructions for booting up Ubuntu in the grub menu.

Here is the result of sudo lshw -C display:

```
  *-display
       description: VGA compatible controller
       product: RV770 [Radeon HD 4870]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:18 memory:c0000000-cfffffff memory:fdce0000-fdceffff ioport:ce00(size=256) memory:fdc00000-fdc1ffff
  *-display
       description: VGA compatible controller
       product: RV770 [Radeon HD 4870]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:19 memory:d0000000-dfffffff memory:fdbe0000-fdbeffff ioport:be00(size=256) memory:fdb00000-fdb1ffff
```

And here is the output to lspci -nnk | grep -iA3 vga:

```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV770 [Radeon HD 4870] [1002:9440]
    Subsystem: PC Partner Limited / Sapphire Technology Device [174b:0851]
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
--
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV770 [Radeon HD 4870] [1002:9440]
    Subsystem: PC Partner Limited / Sapphire Technology Device [174b:0851]
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
```

---

### Post by Bashing-om on 2014-01-23
sir_robert007: well well,

That all looks good, The graphics card(s) are identified, the drivers are available, and more the fglrx drivers are loaded, and you are driving 2 displays.

I recon it is time to look at the logs:
In your /home directory:
```

cat ~/.xsession-errors

```
And the other that might give us direction:
```

cat /var/log/Xorg.0.log

``` as jp had earlier advised.

let's see what tale
[INDENT][INDENT]the logs can tell
[/INDENT][/INDENT]

---

### Post by jeanjd63 on 2014-01-24
Hello
You can try :
[B]sudo  apt-get  update
sudo  apt-get  dist-upgrade[/B]
then
**reboot**

---

### Post by sir_robert007 on 2014-01-24
> **Bashing-om said:**
> sir_robert007: well well,

That all looks good, The graphics card(s) are identified, the drivers are available, and more the fglrx drivers are loaded, and you are driving 2 displays.

I recon it is time to look at the logs:
In your /home directory:
```

cat ~/.xsession-errors

```
And the other that might give us direction:
```

cat /var/log/Xorg.0.log

``` as jp had earlier advised.

let's see what tale[INDENT][INDENT]the logs can tell
[/INDENT]
[/INDENT]


Ok here is the output from .xsession-errors

```
gnome-session[1837]: WARNING: Session 'ubuntu' runnable check failed: Exited with code 1
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-panel: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-panel: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0
unity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F10" 
** Message: moving back from GtkStatusIcon to indicator
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.14.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
unity-2d-shell: [WARNING] libindicator: Desktop file '/usr/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.

** (zeitgeist-datahub:2315): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
[WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://gwibber.desktop" 
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://gwibber.desktop" 

** (nautilus:1950): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist


** (nautilus:1950): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed
unity-2d-shell: [WARNING] void ApplicationsList::remoteEntryUpdated(const QString&, const QString&, const QString&, const QMap<QString, QVariant>&): Application sent an update but we don't seem to have it in the launcher: "application://update-manager.desktop" 
Window manager warning: Treating resize request of legacy application 0x3206b74 (Google Chr) as a fullscreen request
[36:36:1018/132635:ERROR:render_widget_fullscreen_pepper.cc(292)] Not implemented reached in virtual void content::{anonymous}::PepperWidget::setFocus(bool)
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
unity-2d-shell: [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22003cc (w)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
unity-2d-shell: [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3c00003 (168742_104)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
Window manager warning: unity-2d-shellReceived a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
: [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22003cc (w)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [CRITICAL] Wnck: wnck_workspace_activate: assertion `WNCK_IS_WORKSPACE (space)' failed
unity-2d-shell: [CRITICAL] Wnck: wnck_workspace_is_virtual: assertion `WNCK_IS_WORKSPACE (space)' failed
unity-2d-shell: [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3a00003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
ERROR:root:free space check failed
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 762, in on_button_install_clicked
    self.cache.checkFreeSpace()
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeCache.py", line 1167, in checkFreeSpace
    for (dir, size) in [(archivedir, self.requiredDownload),
  File "/usr/lib/python2.7/dist-packages/UpdateManager/Core/MyCache.py", line 98, in requiredDownload
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the libdrm2 package. This might mean you need to manually fix this package.
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
Window manager warning: unity-2d-shellReceived a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
: [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3a00003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: unity-2d-shellReceived a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
: [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22003cc (w)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
Window manager warning: unity-2d-shellReceived a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
: [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3a00003 (Update Man)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1920723128") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1920723128") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1920723128") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1920723128") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1920723128") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1920723128") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1920723128") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1920723128") 
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
unity-2d-shell: [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x22003cc (w)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
unity-2d-shell: [WARNING] Wnck: Received a timestamp of 0; window activation may not function properly.

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3a00003 (29994_1069)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application1830183592") 
[209:215:1018/142439:ERROR:platform_thread_linux.cc(99)] Failed to set nice value of thread to -10
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application2088512325") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application2088512325") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application2088512325") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application2088512325") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application2088512325") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application2088512325") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application2088512325") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application829906520") 
unity-2d-panelunity-2d-shell: [DEBUG] void GnomeSessionClient::queryEndSession(): 
unity-2d-shell: [DEBUG] bool GnomeSessionClientPrivate::sendEndSessionResponse(): 
: [DEBUG] void GnomeSessionClient::queryEndSession(): 
unity-2d-panel: [DEBUG] bool GnomeSessionClientPrivate::sendEndSessionResponse(): 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] libindicator: Unable to load keyfile from file '': No such file or directory
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-panel: [DEBUG] void GnomeSessionClient::waitForEndSession(): Application is about to quit, waiting for gnome-session to call us back 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-panel: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window8388613") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [DEBUG] void GnomeSessionClient::endSession(): 
unity-2d-shell: [DEBUG] bool GnomeSessionClientPrivate::sendEndSessionResponse(): 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.application' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-shell: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0xa8fc30") 
unity-2d-panel: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window8388613") 
unity-2d-panel: [DEBUG] void GnomeSessionClient::endSession(): 
unity-2d-panel: [DEBUG] bool GnomeSessionClientPrivate::sendEndSessionResponse(): 
unity-2d-shell: [DEBUG] void GnomeSessionClient::waitForEndSession(): Application is about to quit, waiting for gnome-session to call us back 
unity-2d-panel: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window8388613") 
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

(gnome-settings-daemon:1888): print-notifications-plugin-CRITICAL **: gsd_print_notifications_plugin_finalize: assertion `plugin->priv != NULL' failed
unity-2d-panel: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window8388613") 
unity-2d-panel: [WARNING] QDBusError("org.freedesktop.DBus.Error.UnknownMethod", "No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window8388613") 

(gnome-settings-daemon:1888): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-settings-daemon:1888): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
unity-2d-shell: [WARNING] QClipboard: Unable to receive an event from the clipboard manager in a reasonable time

(gnome-fallback-mount-helper:1934): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(bluetooth-applet:1953): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nautilus:1950): Gdk-WARNING **: nautilus: Fatal IO error 0 (Success) on X server :0.


(nm-applet:1956): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gdu-notification-daemon:2076): Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(update-notifier:2500): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-screensaver:2282): Gdk-WARNING **: gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(telepathy-indicator:2202): Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(deja-dup-monitor:2614): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.36 of volume monitor org.gtk.Private.GduVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(deja-dup-monitor:2614): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.39 of volume monitor org.gtk.Private.AfcVolumeMonitor disconnected from the bus; removing drives/volumes/mounts

(deja-dup-monitor:2614): GVFS-RemoteVolumeMonitor-WARNING **: Owner :1.42 of volume monitor org.gtk.Private.GPhoto2VolumeMonitor disconnected from the bus; removing drives/volumes/mounts
```

And from Xorg.0.log

```
[     9.636] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[     9.636] X Protocol Version 11, Revision 0
[     9.636] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[     9.636] Current Operating System: Linux hawaii50 3.2.0-54-generic #82-Ubuntu SMP Tue Sep 10 20:08:42 UTC 2013 x86_64
[     9.636] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-54-generic root=UUID=4533f7e6-6c74-4da7-9438-62c30096fb62 ro quiet splash vt.handoff=7
[     9.636] Build Date: 16 October 2013  04:41:23PM
[     9.636] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see http://www.ubuntu.com/support) 
[     9.636] Current version of pixman: 0.24.4
[     9.636]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     9.636] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.636] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 24 17:43:08 2014
[     9.637] (==) Using config file: "/etc/X11/xorg.conf"
[     9.637] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.637] (==) ServerLayout "aticonfig Layout"
[     9.637] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[     9.637] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[     9.637] (**) |   |-->Device "aticonfig-Device[0]-0"
[     9.637] (==) Automatically adding devices
[     9.637] (==) Automatically enabling devices
[     9.637] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.637]     Entry deleted from font path.
[     9.637] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.637]     Entry deleted from font path.
[     9.637] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.637]     Entry deleted from font path.
[     9.638] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.638]     Entry deleted from font path.
[     9.638] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.638]     Entry deleted from font path.
[     9.638] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     9.638]     Entry deleted from font path.
[     9.638] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     9.638] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.638] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.638] (II) Loader magic: 0x7f5ebabfcb00
[     9.638] (II) Module ABI versions:
[     9.638]     X.Org ANSI C Emulation: 0.4
[     9.638]     X.Org Video Driver: 11.0
[     9.638]     X.Org XInput driver : 16.0
[     9.638]     X.Org Server Extension : 6.0
[     9.638] (--) PCI:*(0:1:0:0) 1002:9440:174b:0851 rev 0, Mem @ 0xc0000000/268435456, 0xfdce0000/65536, I/O @ 0x0000ce00/256, BIOS @ 0x????????/131072
[     9.638] (--) PCI: (0:2:0:0) 1002:9440:174b:0851 rev 0, Mem @ 0xd0000000/268435456, 0xfdbe0000/65536, I/O @ 0x0000be00/256, BIOS @ 0x????????/131072
[     9.638] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.638] (II) "extmod" will be loaded by default.
[     9.638] (II) "dbe" will be loaded by default.
[     9.638] (II) "glx" will be loaded by default.
[     9.638] (II) "record" will be loaded by default.
[     9.638] (II) "dri" will be loaded by default.
[     9.639] (II) "dri2" will be loaded by default.
[     9.639] (II) LoadModule: "extmod"
[     9.652] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.652] (II) Module extmod: vendor="X.Org Foundation"
[     9.652]     compiled for 1.11.3, module version = 1.0.0
[     9.652]     Module class: X.Org Server Extension
[     9.652]     ABI class: X.Org Server Extension, version 6.0
[     9.652] (II) Loading extension MIT-SCREEN-SAVER
[     9.652] (II) Loading extension XFree86-VidModeExtension
[     9.652] (II) Loading extension XFree86-DGA
[     9.652] (II) Loading extension DPMS
[     9.652] (II) Loading extension XVideo
[     9.652] (II) Loading extension XVideo-MotionCompensation
[     9.652] (II) Loading extension X-Resource
[     9.652] (II) LoadModule: "dbe"
[     9.652] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.652] (II) Module dbe: vendor="X.Org Foundation"
[     9.652]     compiled for 1.11.3, module version = 1.0.0
[     9.652]     Module class: X.Org Server Extension
[     9.652]     ABI class: X.Org Server Extension, version 6.0
[     9.652] (II) Loading extension DOUBLE-BUFFER
[     9.652] (II) LoadModule: "glx"
[     9.652] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     9.653] (II) Module glx: vendor="X.Org Foundation"
[     9.653]     compiled for 1.11.3, module version = 1.0.0
[     9.653]     ABI class: X.Org Server Extension, version 6.0
[     9.653] (==) AIGLX enabled
[     9.653] (II) Loading extension GLX
[     9.653] (II) LoadModule: "record"
[     9.653] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     9.653] (II) Module record: vendor="X.Org Foundation"
[     9.653]     compiled for 1.11.3, module version = 1.13.0
[     9.653]     Module class: X.Org Server Extension
[     9.653]     ABI class: X.Org Server Extension, version 6.0
[     9.653] (II) Loading extension RECORD
[     9.653] (II) LoadModule: "dri"
[     9.653] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.653] (II) Module dri: vendor="X.Org Foundation"
[     9.653]     compiled for 1.11.3, module version = 1.0.0
[     9.653]     ABI class: X.Org Server Extension, version 6.0
[     9.653] (II) Loading extension XFree86-DRI
[     9.653] (II) LoadModule: "dri2"
[     9.653] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     9.653] (II) Module dri2: vendor="X.Org Foundation"
[     9.653]     compiled for 1.11.3, module version = 1.2.0
[     9.653]     ABI class: X.Org Server Extension, version 6.0
[     9.653] (II) Loading extension DRI2
[     9.653] (II) LoadModule: "fglrx"
[     9.654] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[     9.671] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[     9.671]     compiled for 1.4.99.906, module version = 8.97.2
[     9.671]     Module class: X.Org Video Driver
[     9.671] (II) Loading sub module "fglrxdrm"
[     9.671] (II) LoadModule: "fglrxdrm"
[     9.672] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[     9.672] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     9.672]     compiled for 1.4.99.906, module version = 8.97.2
[     9.672] (II) ATI Proprietary Linux Driver Version Identifier:8.97.2
[     9.672] (II) ATI Proprietary Linux Driver Release Identifier: 8.97.100.7                           
[     9.672] (II) ATI Proprietary Linux Driver Build Date: Nov 16 2012 14:45:00
[     9.672] (++) using VT number 7

[     9.672] (WW) Falling back to old probe method for fglrx
[     9.678] (II) Loading PCS database from /etc/ati/amdpcsdb
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:0) found
[     9.679] (--) Chipset Supported AMD Graphics Processor (0x9440) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:3:0) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:4:0) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:10:0) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[     9.679] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[     9.679] (**) ChipID override: 0x9440
[     9.679] (**) Chipset Supported AMD Graphics Processor (0x9440) found
[     9.681] ukiDynamicMajor: found major device number 249
[     9.681] ukiDynamicMajor: found major device number 249
[     9.681] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     9.681] ukiOpenDevice: node name is /dev/ati/card0
[     9.681] ukiOpenDevice: open result is 8, (OK)
[     9.681] ukiOpenByBusid: ukiOpenMinor returns 8
[     9.681] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     9.764] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[     9.764] (II) AMD Video driver is signed
[     9.764] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[     9.764] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[     9.764] (II) fglrx(0): pEnt->device->identifier=0x7f5ebb8edcb0
[     9.764] (II) pEnt->device->identifier=(nil)
[     9.764] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
[     9.765] (II) Loading sub module "vgahw"
[     9.765] (II) LoadModule: "vgahw"
[     9.804] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[     9.804] (II) Module vgahw: vendor="X.Org Foundation"
[     9.804]     compiled for 1.11.3, module version = 0.1.0
[     9.804]     ABI class: X.Org Video Driver, version 11.0
[     9.804] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     9.804] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     9.804] (==) fglrx(0): Default visual is TrueColor
[     9.804] (**) fglrx(0): Option "DPMS" "true"
[     9.804] (==) fglrx(0): RGB weight 888
[     9.804] (II) fglrx(0): Using 8 bits per RGB 
[     9.804] (==) fglrx(0): Buffer Tiling is ON
[     9.804] (II) Loading sub module "fglrxdrm"
[     9.804] (II) LoadModule: "fglrxdrm"
[     9.804] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[     9.804] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     9.804]     compiled for 1.4.99.906, module version = 8.97.2
[     9.805] ukiDynamicMajor: found major device number 249
[     9.806] ukiDynamicMajor: found major device number 249
[     9.806] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     9.806] ukiOpenDevice: node name is /dev/ati/card0
[     9.806] ukiOpenDevice: open result is 13, (OK)
[     9.806] ukiOpenByBusid: ukiOpenMinor returns 13
[     9.806] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     9.806] ukiDynamicMajor: found major device number 249
[     9.806] ukiDynamicMajor: found major device number 249
[     9.806] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[     9.806] ukiOpenDevice: node name is /dev/ati/card0
[     9.806] ukiOpenDevice: open result is 14, (OK)
[     9.806] ukiOpenByBusid: ukiOpenMinor returns 14
[     9.806] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     9.806] ukiOpenDevice: node name is /dev/ati/card1
[     9.806] ukiOpenDevice: open result is 14, (OK)
[     9.806] ukiOpenByBusid: ukiOpenMinor returns 14
[     9.806] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[     9.806] (**) fglrx(0): NoAccel = NO
[     9.806] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
[     9.806] (--) fglrx(0): Chipset: "ATI Radeon HD 4800 Series        " (Chipset = 0x9440)
[     9.806] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x0851)
[     9.806] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[     9.806] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[     9.806] (--) fglrx(0): MMIO registers at 0xfdce0000
[     9.806] (--) fglrx(0): I/O port at 0x0000ce00
[     9.806] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     9.896] (II) fglrx(0): AC Adapter is used
[     9.900] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[     9.901] (II) Loading sub module "vbe"
[     9.901] (II) LoadModule: "vbe"
[     9.901] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     9.901] (II) Module vbe: vendor="X.Org Foundation"
[     9.901]     compiled for 1.11.3, module version = 1.1.0
[     9.902]     ABI class: X.Org Video Driver, version 11.0
[     9.902] (II) fglrx(0): VESA BIOS detected
[     9.902] (II) fglrx(0): VESA VBE Version 3.0
[     9.902] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[     9.902] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[     9.902] (II) fglrx(0): VESA VBE OEM Software Rev: 11.12
[     9.902] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[     9.902] (II) fglrx(0): VESA VBE OEM Product: RV770
[     9.902] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[     9.938] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[     9.938] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[     9.938] (II) fglrx(0): PCIE card detected
[     9.938] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     9.938] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     9.938] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x0851)
[     9.938] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[     9.938] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[     9.938] (--) fglrx(0): MMIO registers at 0xfdbe0000
[     9.938] (--) fglrx(0): I/O port at 0x0000be00
[     9.938] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     9.939] (II) fglrx(0): AC Adapter is used
[     9.941] (II) fglrx(0): Invalid ATI BIOS from int10, the adapter is not VGA-enabled
[    10.200] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    10.200] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    10.200] (II) fglrx(0): PCIE card detected
[    10.200] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    10.200] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    10.201] (II) fglrx(0): Using adapter: 1:0.0.
[    10.238] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    10.247] (II) fglrx(0): Interrupt handler installed at IRQ 47.
[    10.247] (II) fglrx(0): Using adapter: 2:0.0.
[    10.253] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    10.262] (II) fglrx(0): RandR 1.2 support is enabled!
[    10.262] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    10.262] (==) fglrx(0): Center Mode is disabled 
[    10.262] (II) Loading sub module "fb"
[    10.262] (II) LoadModule: "fb"
[    10.262] (II) Loading /usr/lib/xorg/modules/libfb.so
[    10.263] (II) Module fb: vendor="X.Org Foundation"
[    10.263]     compiled for 1.11.3, module version = 1.0.0
[    10.263]     ABI class: X.Org ANSI C Emulation, version 0.4
[    10.263] (II) Loading sub module "ddc"
[    10.263] (II) LoadModule: "ddc"
[    10.263] (II) Module "ddc" already built-in
[    11.296] (II) fglrx(0): Finished Initialize PPLIB!
[    11.800] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[    11.800] (II) fglrx(0): Output DFP2 has no monitor section
[    11.800] (II) fglrx(0): Output CRT1 has no monitor section
[    11.800] (II) fglrx(0): Output CRT2 has no monitor section
[    11.800] (II) fglrx(0): Output TV has no monitor section
[    11.800] (II) fglrx(0): Output CV has no monitor section
[    11.800] (II) Loading sub module "ddc"
[    11.800] (II) LoadModule: "ddc"
[    11.800] (II) Module "ddc" already built-in
[    11.800] (II) fglrx(0): Connected Display0: DFP1
[    11.800] (II) fglrx(0): Display0 EDID data ---------------------------
[    11.800] (II) fglrx(0): Manufacturer: ACI  Model: 23f2  Serial#: 215300
[    11.800] (II) fglrx(0): Year: 2009  Week: 53
[    11.800] (II) fglrx(0): EDID Version: 1.3
[    11.800] (II) fglrx(0): Digital Display Input
[    11.800] (II) fglrx(0): Max Image Size [cm]: horiz.: 52  vert.: 29
[    11.800] (II) fglrx(0): Gamma: 2.20
[    11.800] (II) fglrx(0): DPMS capabilities: Off
[    11.800] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    11.800] (II) fglrx(0): First detailed timing is preferred mode
[    11.800] (II) fglrx(0): redX: 0.644 redY: 0.332   greenX: 0.286 greenY: 0.601
[    11.800] (II) fglrx(0): blueX: 0.152 blueY: 0.076   whiteX: 0.312 whiteY: 0.328
[    11.800] (II) fglrx(0): Supported established timings:
[    11.800] (II) fglrx(0): 720x400@70Hz
[    11.800] (II) fglrx(0): 640x480@60Hz
[    11.800] (II) fglrx(0): 640x480@67Hz
[    11.800] (II) fglrx(0): 640x480@72Hz
[    11.800] (II) fglrx(0): 640x480@75Hz
[    11.800] (II) fglrx(0): 800x600@56Hz
[    11.800] (II) fglrx(0): 800x600@60Hz
[    11.800] (II) fglrx(0): 800x600@72Hz
[    11.800] (II) fglrx(0): 800x600@75Hz
[    11.800] (II) fglrx(0): 832x624@75Hz
[    11.800] (II) fglrx(0): 1024x768@60Hz
[    11.800] (II) fglrx(0): 1024x768@70Hz
[    11.800] (II) fglrx(0): 1024x768@75Hz
[    11.800] (II) fglrx(0): 1280x1024@75Hz
[    11.800] (II) fglrx(0): Manufacturer's mask: 0
[    11.800] (II) fglrx(0): Supported standard timings:
[    11.800] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    11.800] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    11.800] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    11.800] (II) fglrx(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    11.800] (II) fglrx(0): #4: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    11.800] (II) fglrx(0): Supported detailed timing:
[    11.800] (II) fglrx(0): clock: 148.5 MHz   Image Size:  521 x 293 mm
[    11.800] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    11.800] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    11.800] (II) fglrx(0): Serial No: 9CLMTF215300
[    11.800] (II) fglrx(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 85 kHz, PixClock max 165 MHz
[    11.800] (II) fglrx(0): Monitor name: ASUS VH236H
[    11.800] (II) fglrx(0): EDID (in hex):
[    11.800] (II) fglrx(0):     00ffffffffffff000469f22304490300
[    11.800] (II) fglrx(0):     3513010380341d782ac720a455499927
[    11.800] (II) fglrx(0):     135054bfef00714f81809500b300d1c0
[    11.800] (II) fglrx(0):     010101010101023a801871382d40582c
[    11.800] (II) fglrx(0):     450009252100001e000000ff0039434c
[    11.800] (II) fglrx(0):     4d54463231353330300a000000fd0037
[    11.800] (II) fglrx(0):     4b1e5510000a202020202020000000fc
[    11.800] (II) fglrx(0):     0041535553205648323336480a2000b5
[    11.800] (II) fglrx(0): End of Display0 EDID data --------------------
[    12.020] (II) fglrx(0): EDID for output DFP1
[    12.020] (II) fglrx(0): Manufacturer: ACI  Model: 23f2  Serial#: 215300
[    12.020] (II) fglrx(0): Year: 2009  Week: 53
[    12.020] (II) fglrx(0): EDID Version: 1.3
[    12.020] (II) fglrx(0): Digital Display Input
[    12.020] (II) fglrx(0): Max Image Size [cm]: horiz.: 52  vert.: 29
[    12.020] (II) fglrx(0): Gamma: 2.20
[    12.020] (II) fglrx(0): DPMS capabilities: Off
[    12.020] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    12.020] (II) fglrx(0): First detailed timing is preferred mode
[    12.020] (II) fglrx(0): redX: 0.644 redY: 0.332   greenX: 0.286 greenY: 0.601
[    12.020] (II) fglrx(0): blueX: 0.152 blueY: 0.076   whiteX: 0.312 whiteY: 0.328
[    12.020] (II) fglrx(0): Supported established timings:
[    12.020] (II) fglrx(0): 720x400@70Hz
[    12.020] (II) fglrx(0): 640x480@60Hz
[    12.020] (II) fglrx(0): 640x480@67Hz
[    12.020] (II) fglrx(0): 640x480@72Hz
[    12.020] (II) fglrx(0): 640x480@75Hz
[    12.020] (II) fglrx(0): 800x600@56Hz
[    12.020] (II) fglrx(0): 800x600@60Hz
[    12.020] (II) fglrx(0): 800x600@72Hz
[    12.020] (II) fglrx(0): 800x600@75Hz
[    12.020] (II) fglrx(0): 832x624@75Hz
[    12.020] (II) fglrx(0): 1024x768@60Hz
[    12.020] (II) fglrx(0): 1024x768@70Hz
[    12.020] (II) fglrx(0): 1024x768@75Hz
[    12.020] (II) fglrx(0): 1280x1024@75Hz
[    12.020] (II) fglrx(0): Manufacturer's mask: 0
[    12.020] (II) fglrx(0): Supported standard timings:
[    12.020] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    12.020] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    12.020] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    12.020] (II) fglrx(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    12.020] (II) fglrx(0): #4: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    12.020] (II) fglrx(0): Supported detailed timing:
[    12.020] (II) fglrx(0): clock: 148.5 MHz   Image Size:  521 x 293 mm
[    12.020] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    12.020] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    12.020] (II) fglrx(0): Serial No: 9CLMTF215300
[    12.020] (II) fglrx(0): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 85 kHz, PixClock max 165 MHz
[    12.020] (II) fglrx(0): Monitor name: ASUS VH236H
[    12.020] (II) fglrx(0): EDID (in hex):
[    12.020] (II) fglrx(0):     00ffffffffffff000469f22304490300
[    12.020] (II) fglrx(0):     3513010380341d782ac720a455499927
[    12.020] (II) fglrx(0):     135054bfef00714f81809500b300d1c0
[    12.020] (II) fglrx(0):     010101010101023a801871382d40582c
[    12.020] (II) fglrx(0):     450009252100001e000000ff0039434c
[    12.020] (II) fglrx(0):     4d54463231353330300a000000fd0037
[    12.020] (II) fglrx(0):     4b1e5510000a202020202020000000fc
[    12.020] (II) fglrx(0):     0041535553205648323336480a2000b5
[    12.020] (II) fglrx(0): EDID vendor "ACI", prod id 9202
[    12.020] (II) fglrx(0): Using EDID range info for horizontal sync
[    12.020] (II) fglrx(0): Using EDID range info for vertical refresh
[    12.020] (II) fglrx(0): Printing DDC gathered Modelines:
[    12.020] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    12.020] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.020] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    12.020] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    12.020] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    12.020] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    12.020] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.020] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    12.020] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    12.020] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    12.020] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    12.020] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.020] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    12.020] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    12.020] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    12.020] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    12.020] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    12.020] (II) fglrx(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    12.020] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    12.020] (II) fglrx(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    12.020] (II) fglrx(0): Printing probed modes for output DFP1
[    12.020] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz)
[    12.020] (II) fglrx(0): Modeline "1776x1000"x60.0  147.05  1776 1880 2072 2368  1000 1001 1004 1035 +hsync -vsync (62.1 kHz)
[    12.020] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 -hsync -vsync (60.0 kHz)
[    12.020] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    12.020] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    12.020] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    12.020] (II) fglrx(0): Modeline "1360x1024"x60.0  116.01  1360 1448 1592 1824  1024 1025 1028 1060 +hsync -vsync (63.6 kHz)
[    12.020] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    12.020] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    12.020] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    12.021] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    12.021] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    12.021] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    12.021] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    12.021] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    12.021] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    12.021] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    12.021] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    12.021] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    12.021] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    12.021] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    12.021] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    12.021] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    12.021] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    12.021] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    12.021] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    12.021] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    12.021] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    12.021] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    12.021] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    12.021] (II) fglrx(0): EDID for output DFP2
[    12.021] (II) fglrx(0): EDID for output CRT1
[    12.021] (II) fglrx(0): EDID for output CRT2
[    12.021] (II) fglrx(0): EDID for output TV
[    12.021] (II) fglrx(0): EDID for output CV
[    12.021] (II) fglrx(0): Output DFP1 connected
[    12.021] (II) fglrx(0): Output DFP2 disconnected
[    12.021] (II) fglrx(0): Output CRT1 disconnected
[    12.021] (II) fglrx(0): Output CRT2 disconnected
[    12.021] (II) fglrx(0): Output TV disconnected
[    12.021] (II) fglrx(0): Output CV disconnected
[    12.021] (II) fglrx(0): Using exact sizes for initial modes
[    12.021] (II) fglrx(0): Output DFP1 using initial mode 1920x1080
[    12.021] (II) fglrx(0): Display dimensions: (520, 290) mm
[    12.021] (II) fglrx(0): DPI set to (94, 94)
[    12.021] (II) fglrx(0): Adapter ATI Radeon HD 4800 Series         has 2 configurable heads and 1 displays connected.
[    12.021] (==) fglrx(0):  PseudoColor visuals disabled
[    12.021] (II) Loading sub module "ramdac"
[    12.021] (II) LoadModule: "ramdac"
[    12.021] (II) Module "ramdac" already built-in
[    12.021] (==) fglrx(0): NoDRI = NO
[    12.021] (==) fglrx(0): Capabilities: 0x00000000
[    12.021] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    12.021] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    12.021] (==) fglrx(0): UseFastTLS=0
[    12.021] (==) fglrx(0): BlockSignalsOnLock=1
[    12.021] (--) Depth 24 pixmap format is 32 bpp
[    12.024] (II) Loading extension ATIFGLRXDRI
[    12.024] (II) fglrx(0): doing swlDriScreenInit
[    12.024] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    12.025] ukiDynamicMajor: found major device number 249
[    12.025] ukiDynamicMajor: found major device number 249
[    12.025] ukiDynamicMajor: found major device number 249
[    12.025] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    12.025] ukiOpenDevice: node name is /dev/ati/card0
[    12.025] ukiOpenDevice: open result is 19, (OK)
[    12.025] ukiOpenByBusid: ukiOpenMinor returns 19
[    12.025] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    12.025] (II) fglrx(0): [uki] DRM interface version 1.0
[    12.025] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    12.025] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    12.025] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f5eb5409000
[    12.025] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    12.025] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    12.025] (II) fglrx(0): swlDriScreenInit done
[    12.025] (II) fglrx(0): Kernel Module Version Information:
[    12.025] (II) fglrx(0):     Name: fglrx
[    12.025] (II) fglrx(0):     Version: 8.97.2
[    12.025] (II) fglrx(0):     Date: Nov 16 2012
[    12.025] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    12.025] (II) fglrx(0): Kernel Module version matches driver.
[    12.025] (II) fglrx(0): Kernel Module Build Time Information:
[    12.025] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.2.0-54-generic
[    12.025] (II) fglrx(0):     Build-Kernel MODVERSIONS:        no
[    12.025] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    12.025] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    12.025] (II) fglrx(0): [uki] register handle = 0x00004000
[    12.038] (II) fglrx(0): DRI initialization successfull
[    12.038] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01068000
```

---

### Post by Bashing-om on 2014-01-24
sir_robert007; Welp.

Upfront, a lot of the errors and indicators I do not understand.
But we do know that the system is not happy with the driver's config file.
Let's move it out of the way and will generate a new one when we do reboot:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
and now let's initialize the driver:
```

sudo amdconfig --initial

```

Reboot now and let's see what happened.

Else we are to consider removing the drivers, and seeing if we can come up on the open source drivers, Then see about installing proprietary drivers from that foundation.

[INDENT][INDENT][INDENT]some times I do wonder
[INDENT][INDENT][INDENT]othertimes, I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sir_robert007 on 2014-01-25
> **Bashing-om said:**
> sir_robert007; Welp.

Upfront, a lot of the errors and indicators I do not understand.
But we do know that the system is not happy with the driver's config file.
Let's move it out of the way and will generate a new one when we do reboot:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
and now let's initialize the driver:
```

sudo amdconfig --initial

```

Reboot now and let's see what happened.

Else we are to consider removing the drivers, and seeing if we can come up on the open source drivers, Then see about installing proprietary drivers from that foundation.

[INDENT][INDENT][INDENT]some times I do wonder
[INDENT][INDENT][INDENT]othertimes, I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]
.
Ok I tried your idea. X is still not starting.

---

### Post by Bashing-om on 2014-01-25
sir_robert007; OK ,

Let's reduce to simplest terms, and 
Start from scratch.
Disconnect the secondary display - will deal with it later.

Remove all the drivers and come back up on open source:
1. If you installed fglrx from the repo, do
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates

```

2. If you installed using a package from AMD/ATI's website
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo amdconfig --uninstall
sudo apt-get install dkms
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u

```

Reboot;
Now advise on where we are, and what is yet to be done,

[INDENT][INDENT]we be try'n
[/INDENT][/INDENT]

---

### Post by sir_robert007 on 2014-01-26
> **Bashing-om said:**
> sir_robert007; OK ,

Let's reduce to simplest terms, and 
Start from scratch.
Disconnect the secondary display - will deal with it later.

Remove all the drivers and come back up on open source:
1. If you installed fglrx from the repo, do
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get purge fglrx fglrx-amdcccle fglrx-updates fglrx-amdcccle-updates

```

2. If you installed using a package from AMD/ATI's website
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo amdconfig --uninstall
sudo apt-get install dkms
sudo apt-get install xserver-xorg-video-nouveau
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo update-initramfs -u

```

Reboot;
Now advise on where we are, and what is yet to be done,
[INDENT][INDENT]we be try'n
[/INDENT]
[/INDENT]


Yes! It worked!! Got X to start and the desktop seems to be working just fine. Thanks for your help! I plan on just sticking with the open source drivers for now as the AMD legacy drivers are a bit buggy after they pulled support for the HD 4000 series of graphics cards.

Thanks again for the help.

---

### Post by Bashing-om on 2014-01-26
sir_robert007; Hey ! Outstanding !

You may now kick me in the backside for not seeing and making that realization early on in the process !
Yeah. AMD has dropped support for that card in later versions of ubuntu.

If it comes a time where you do require the fglrx driver, you will have to install version 12.04.1 as that version does have the stack (X-server) that AMD supports. 12.04.1 is still a Long Term Support version and will have continued support 'till 2017.

[INDENT][INDENT]happy trails to you 
[/INDENT][/INDENT]

---

