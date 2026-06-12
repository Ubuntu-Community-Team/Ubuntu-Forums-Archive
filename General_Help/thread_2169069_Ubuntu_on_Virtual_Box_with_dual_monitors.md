---
title: "Ubuntu on Virtual Box with dual monitors"
date: 2013-08-20
forum: General Help
---

### Post by bartek3 on 2013-08-20
Hello,

I'm using Ubuntu 13.04 on my Virtual Box (Windows 7 host). It worked fine for couple of months with video hardware acelleration, Unity, Compiz etc. Yesterday I connected second monitor to my computer and enabled it in Virtual Box. Ubuntu starts ok with login screen, but after login it shows only desktop wallpaper on one monitor. Second one is all black.

I can get it work by:

```
$ unity --replace
```

but windows have no title bar (not maxmized windows). Maximized windows are connected with the top bar.

.xsession-errors after login (before unity restart) looks like this:

```
Script for cjkv started at run_im.
Script for default started at run_im.
openConnection: connect: Nie ma takiego pliku ani katalogu
cannot connect to brltty at :0
Script for cjkv started at run_im.
Script for default started at run_im.
gnome-session[2003]: EggSMClient-WARNING: Desktop file '/home/bartek/.config/autostart/everpad.desktop' has malformed Icon key 'everpad.png'(should not include extension)
OpenGL Warning: glFlushVertexArrayRangeNV not found in mesa table
OpenGL Warning: glVertexArrayRangeNV not found in mesa table
OpenGL Warning: glCombinerInputNV not found in mesa table
OpenGL Warning: glCombinerOutputNV not found in mesa table
OpenGL Warning: glCombinerParameterfNV not found in mesa table
OpenGL Warning: glCombinerParameterfvNV not found in mesa table
OpenGL Warning: glCombinerParameteriNV not found in mesa table
OpenGL Warning: glCombinerParameterivNV not found in mesa table
OpenGL Warning: glFinalCombinerInputNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterivNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glDeleteFencesNV not found in mesa table
OpenGL Warning: glFinishFenceNV not found in mesa table
OpenGL Warning: glGenFencesNV not found in mesa table
OpenGL Warning: glGetFenceivNV not found in mesa table
OpenGL Warning: glIsFenceNV not found in mesa table
OpenGL Warning: glSetFenceNV not found in mesa table
OpenGL Warning: glTestFenceNV not found in mesa table
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
OpenGL Warning: glFlushVertexArrayRangeNV not found in mesa table
OpenGL Warning: glVertexArrayRangeNV not found in mesa table
OpenGL Warning: glCombinerInputNV not found in mesa table
OpenGL Warning: glCombinerOutputNV not found in mesa table
OpenGL Warning: glCombinerParameterfNV not found in mesa table
OpenGL Warning: glCombinerParameterfvNV not found in mesa table
OpenGL Warning: glCombinerParameteriNV not found in mesa table
OpenGL Warning: glCombinerParameterivNV not found in mesa table
OpenGL Warning: glFinalCombinerInputNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterivNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glDeleteFencesNV not found in mesa table
OpenGL Warning: glFinishFenceNV not found in mesa table
OpenGL Warning: glGenFencesNV not found in mesa table
OpenGL Warning: glGetFenceivNV not found in mesa table
OpenGL Warning: glIsFenceNV not found in mesa table
OpenGL Warning: glSetFenceNV not found in mesa table
OpenGL Warning: glTestFenceNV not found in mesa table
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
OpenGL Warning: glFlushVertexArrayRangeNV not found in mesa table
OpenGL Warning: glVertexArrayRangeNV not found in mesa table
OpenGL Warning: glCombinerInputNV not found in mesa table
OpenGL Warning: glCombinerOutputNV not found in mesa table
OpenGL Warning: glCombinerParameterfNV not found in mesa table
OpenGL Warning: glCombinerParameterfvNV not found in mesa table
OpenGL Warning: glCombinerParameteriNV not found in mesa table
OpenGL Warning: glCombinerParameterivNV not found in mesa table
OpenGL Warning: glFinalCombinerInputNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterfvNV not found in mesa table
OpenGL Warning: glGetCombinerOutputParameterivNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterfvNV not found in mesa table
OpenGL Warning: glGetFinalCombinerInputParameterivNV not found in mesa table
OpenGL Warning: glDeleteFencesNV not found in mesa table
OpenGL Warning: glFinishFenceNV not found in mesa table
OpenGL Warning: glGenFencesNV not found in mesa table
OpenGL Warning: glGetFenceivNV not found in mesa table
OpenGL Warning: glIsFenceNV not found in mesa table
OpenGL Warning: glSetFenceNV not found in mesa table
OpenGL Warning: glTestFenceNV not found in mesa table
OpenGL Warning: No pincher, please call crStateSetCurrentPointers() in your SPU
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
OpenGL Info: Using XSHM for GLX_EXT_texture_from_pixmap
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/bartek/.compiz/session/10200f331e10faa7f5137701252269630900000020030042"
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: unityshell
** Message: applet now removed from the notification area
compiz (core) - Info: Starting plugin: unityshell
** Message: using fallback from indicator to GtkStatusIcon

(nautilus:2205): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(nautilus:2205): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed
** Message: moving back from GtkStatusIcon to indicator

** (nm-applet:2213): WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries

** (nautilus:2205): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist


** (nautilus:2205): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed
```


After disabling second monitor in Virtual Box Unity works normally, again.

---

### Post by lukeiamyourfather on 2013-08-20
Last I looked into it the multiple virtual monitors were only supported on Windows guests. The documentation doesn't seem to indicate support for any other guest platforms and gives only Windows as an example.

---

