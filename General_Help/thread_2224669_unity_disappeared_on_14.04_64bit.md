---
title: "unity disappeared on 14.04 64bit"
date: 2014-05-17
forum: General Help
---

### Post by gore-amit on 2014-05-17
i had my ubuntu and unity working.
suddenly i cant see any unity or launcher. i can see desktop files but not launcher.

i am posting this thread from other machine.
so i would be able to TYPE outputs pf few of the commands.

i executed setsid unity and i got following messages:
WARNING no DISPLAY variable set, setting it to :0
stop: Unknown job : unity-panel-service
and GLib-WARNING
and
compiz (core) - Error: Plugin 'opengl' not loaded.

---

### Post by gore-amit on 2014-05-17
i am onto same system but with LiveUSB. so let me know if i can send/share any command outputs.
Just to elaborate more onto issue. I am able to log onto my acer laptop.
I can see icons on my desktop. I can see a "temperature" program starting. However there is no 'title bar and minimize, close buttons".
I right clicked and open "Control/Settings". But it doesnot show title bar ie to close/minimize buttons.

---

### Post by grahammechanical on 2014-05-17
Do you have Compiz Configuration Settings Manager installed and did you disable the Unity plugin? There are a couple of other commands to try as well as setsid unity. To reset Compiz

```
dconf reset -f /org/compiz/
```

and

```
unity --reset-icons
```

Regards

---

### Post by philinux on 2014-05-17
[http://m.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html?](http://m.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html?)

Sounds like some settings are messed up. Try resetting unity and compiz back to default
Scroll down the page to the dconf bit.

---

### Post by gore-amit on 2014-05-18
Thank you for reply.
I have checked and sure that unity is enabled. I also enabled other ie opengl, composite.
however no help.

@philinux
i tried other link
unity-reset says command not found.

dconf reset -f /org/compiz/
says error: Cannot autolaunch D-Bus without X11 $DISPLAY

on setting display as:
export DISPLAY=:0
and running above command got
compiz message with error plugin 'OpenGL' not loaded

---

### Post by gore-amit on 2014-05-18
Here is update.
I did not get unity.
so went to text mode and executed a command. and then back to gui with ctl+alt+f7 i can see unity.
but no top panel.
also on rebooting i am on same state.
i dont get the title bar of any windows/application that i invoke.

---

### Post by gore-amit on 2014-05-18
sonal@sonal-Aspire-E1-530:~/unity-revamp-stable$ unity
unity                       unity-tweak-tool
unity-control-center        unity-webapps-desktop-file
unity-greeter               unity-webapps-qml-launcher
unity-scope-loader          unity-webapps-runner
unity-settings-daemon       
sonal@sonal-Aspire-E1-530:~/unity-revamp-stable$ unity
stop: Unknown job: unity-panel-service
start: Unknown job: unity-panel-service
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity

(process:8176): GLib-WARNING **: In call to g_spawn_sync(), exit status of a child process was requested but ECHILD was received by waitpid(). Most likely the process is ignoring SIGCHLD, or some other thread is invoking waitpid() with a nonpositive first argument; either behavior can break applications that use g_spawn_sync either directly or indirectly.
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2014-05-18 14:18:23 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
ERROR 2014-05-18 14:18:23 unity.debug.interface DebugDBusInterface.cpp:196 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: cannot open shared object file: No such file or directory
ERROR 2014-05-18 14:18:24 unityo (appinfo2) <unknown>:0 g_file_monitor_set_rate_limit: assertion 'G_IS_FILE_MONITOR (monitor)' failed
ERROR 2014-05-18 14:18:24 unity.launcher.icon.trash TrashLauncherIcon.cpp:66 Could not create file monitor for trash uri: Operation not supported
WARN  2014-05-18 14:18:24 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Launcher' yet as we don't have a connection, waiting for it...
WARN  2014-05-18 14:18:25 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Dash' yet as we don't have a connection, waiting for it...
WARN  2014-05-18 14:18:25 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.SessionManager.EndSessionDialog' yet as we don't have a connection, waiting for it...
WARN  2014-05-18 14:18:25 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'com.canonical.Unity.Session' yet as we don't have a connection, waiting for it...
WARN  2014-05-18 14:18:25 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.ScreenSaver' yet as we don't have a connection, waiting for it...
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
ERROR 2014-05-18 14:18:26 unity.shell.compiz unityshell.cpp:2719 Decoration plugin is active, disabling it...
compiz (core) - Info: Unloading plugin: decor
ERROR 2014-05-18 14:18:26 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'org.gnome.Shell'
ERROR 2014-05-18 14:18:26 unity.glib.dbus.server GLibDBusServer.cpp:524 DBus name lost 'com.canonical.Unity'
WARN  2014-05-18 14:18:26 unity.glib.dbus.proxy GLibDBusProxy.cpp:417 Calling method "CanShutdown" on object path: "/org/gnome/SessionManager" failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
ERROR 2014-05-18 14:18:26 unity.session.gnome GnomeSessionManager.cpp:340 Gnome Session call failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

---

### Post by gore-amit on 2014-05-18
somehow after executing many commands i have got unity and launcher.
however now i cant see all the applications or settings.
attaching the screenshots.

[ATTACH=CONFIG]253260[/ATTACH]

---

### Post by gore-amit on 2014-05-19
fixed this too.
but still not sure which all commands fixed it.

---

