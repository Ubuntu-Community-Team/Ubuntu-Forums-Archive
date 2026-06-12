---
title: "Unity Launcher and Menu Bar disappeared in 14.04"
date: 2015-02-02
forum: General Help
---

### Post by ricardo30 on 2015-02-02
I recently installed the ATI driver and after a reboot I had an empty desktop. I think is the same probleme than here: [http://askubuntu.com/questions/26072...ing-on-startup]("http://askubuntu.com/questions/260727/libgl-error-unity-and-compiz-not-loading-on-startup") but there's no solution. Please help!!

---

### Post by Peptid on 2015-02-03
Hi,
You may want to check this solution as well. [http://askubuntu.com/questions/495997/how-to-properly-restart-unity](http://askubuntu.com/questions/495997/how-to-properly-restart-unity) 
Hope this helps.

---

### Post by slickymaster on 2015-02-03
Also: [Unity doesn't load, no Launcher, no Dash appears]("http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears")

---

### Post by ricardo30 on 2015-02-04
> **Peptid said:**
> Hi,
You may want to check this solution as well. [http://askubuntu.com/questions/495997/how-to-properly-restart-unity](http://askubuntu.com/questions/495997/how-to-properly-restart-unity) 
Hope this helps.

Thanks. didn't work. I typed unity and hit enter as sugested and got the following:


rvg@Chompu:~/Escritorio/Carpeta sin título$ unity
unity-panel-service stop/waiting
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service start/running, process 3988
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
libGL error: dlopen /usr/lib/i386-linux-gnu/dri/swrast_dri.so failed (/usr/lib/i386-linux-gnu/dri/swrast_dri.so: wrong ELF class: ELFCLASS32)
libGL error: failed to load driver: swrast
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
WARN  2015-02-04 16:16:41 unity.glib.dbus.server GLibDBusServer.cpp:579 Can't register object 'org.gnome.Shell' yet as we don't have a connection, waiting for it...
ERROR 2015-02-04 16:16:42 unity.debug.interface DebugDBusInterface.cpp:216 Unable to load entry point in libxpathselect: libxpathselect.so.1.4: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
compiz (unityshell) - Error: GL_ARB_vertex_buffer_object not supported

ERROR 2015-02-04 16:16:42 unity.shell.compiz unityshell.cpp:3865 Impossible to delete the unity locked stamp file
compiz (core) - Error: Plugin initScreen failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x300000b
  Serial number of failed request:  9498
  Current serial number in output stream:  9500

---

### Post by el Arm on 2015-03-27
Not sure if you solved this but I've just had this exact problem in 14.04.

In fact semi-regularly I get either

1. this problem of no window decorations and no panel/launcher or
2. a low-graphics warning after the splash screen (almost worse as I have no desktop, but can access the other terminals with Ctrl+Alt+F2 etc.)

They usually occur after a kernel update.  Tonight it occurred, I think, after a minor update of some mesa libraries.

Loosely the problem is the graphics driver is corrupted or out of sync with Ubuntu libraries, so you have no 3D rendering which Unity 3D relies upon.  If you run fglrxinfo;

```

libGL error: dlopen /usr/lib/i386-linux-gnu/dri/swrast_dri.so failed (/usr/lib/i386-linux-gnu/dri/swrast_dri.so: wrong ELF class: ELFCLASS32)
libGL error: failed to load driver: swrast
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon R9 200 Series     
OpenGL version string: 1.4 (2.1 (4.3.12798 Compatibility Profile Context 13.35.1005))
```

To me it looks like it has got 32-bit rather than 64-bit.  The solution for me is to reinstall the drivers manually (in your case perhaps you have to revert to an earlier version).  I had no luck originally with the open source drivers and consequently I have the AMD 14.20 drivers downloaded, so
```

cd ~/bin/fglrx14.20/
sudo ./amd-driver-installer-14.20-x86.x86_64.run
```

I ignore the warning, then choose "Install driver" (the non-recommended option).  After this, reboot and fglrxinfo should report success.

There is one more item to check.  Install;

```

sudo apt-get install compizconfig-settings-manager
```

Run ccsm from the terminal, go to Desktop > Ubuntu Unity Plugin and in there make sure "Enable Ubuntu Unity Plugin" is checked.   Close it.

At this point you can run
```

unity --replace
```
to start up the unity desktop and hopefully all is well.

If you don't already have a terminal to do all the above (especially ccsm), then from one of the console logins I created a ~/Desktop/Terminal.desktop file with Exec=gnome-terminal in it.  This gives you a desktop icon which will start a (borderless) terminal.  Inside here you can run;

```

sudo apt-get install metacity
metacity --replace
```

so at least you get window borders and a panel to work with in the interim.

---

